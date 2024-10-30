Part-A:

The MD input files, parameter files, and topology files can be found in MD.zip file.

One can run the MD using the following steps.

Energy Minimization

gmx_mpi grompp -f em.mdp -c TMA.gro -p topol_TMA.top  -o em_TMA.tpr

gmx_mpi mdrun -deffnm em_TMA

NPT Equilibration

gmx_mpi grompp -f npt-equilibrium.mdp -c em_TMA.gro -p topol-TMA.top -o npt-TMA.tpr

gmx_mpi mdrun -deffnm npt-TMA

NVT Equilibration

gmx_mpi grompp -f nvt-equilibrium.mdp -c npt-TMA.gro -p topol_TMA.top  -t npt-TMA.cpt -o nvt-TMA.tpr

gmx_mpi mdrun -deffnm nvt-TMA

NVT Prduction Run

gmx_mpi grompp -f production_run_nvt.mdp -c nvt-TMA.gro -p topol_TMA.top -t nvt-TMA.cpt -o nvt-production.tpr

gmx_mpi mdrun -deffnm nvt-production

After performing Part-A, one needs to follow the Part-B for subsequent analysis

Part-B:

The codes and corresponding input files are in the All_Program.zip file in code. First unzip the xdrf directory, then compile the program by

f95 ./xdrf/xtciof.o ./xdrf/libxdrf.a -lm Program.F90

following by ./a.out <file.inp

If one has trajectory file then he/she can easily complie the program.
