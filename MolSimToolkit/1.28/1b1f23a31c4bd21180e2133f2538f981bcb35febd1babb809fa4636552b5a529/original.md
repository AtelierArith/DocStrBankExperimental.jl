```
get_frame(simulation::Simulation, iframe::Integer)
```

Returns the frame at the given index in the trajectory. 

## Example

```julia-repl
julia> using MolSimToolkit, MolSimToolkit.Testing, PDBTools

julia> sim = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> frame4 = get_frame(sim, 4)
   Array{Atoms,1} with 20465 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ILE     P      211        1   -0.397   12.048   37.441  1.00  0.00     1    PROT         1
       2  HT1     ILE     P      211        1   -0.779   11.123   37.726  1.00  0.00     1    PROT         2
       3  HT2     ILE     P      211        1   -0.393   12.662   38.280  1.00  0.00     1    PROT         3
                                                       ⋮ 
   20463  SOD     SOD     S       13     4374  -11.686   23.749   19.935  1.00  0.00     1     SOD     20463
   20464  SOD     SOD     S       14     4375  -34.214   38.148   55.179  1.00  0.00     1     SOD     20464
   20465  SOD     SOD     S       15     4376    7.220  -52.702   66.223  1.00  0.00     1     SOD     20465

julia> writePDB(frame4, "frame4.pdb")
```

!!! note
    The `get_frame` function will read the frames in the trajectory until the desired frame is reached.  This can be slow for large trajectories. If the required frame is before the current frame of the  simulation, the simulation will be restarted. The simulation object is returned positioned in the required frame.

