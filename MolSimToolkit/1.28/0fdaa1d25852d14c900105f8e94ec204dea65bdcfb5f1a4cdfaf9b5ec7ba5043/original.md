```
ss_map(
    simulation::Simulation; 
    selection::Union{AbstractString,Function}=PDBTools.isprotein,
    ss_method=stride_run,
    show_progress=true
)
```

Calculates the secondary structure map of the trajectory.  Returns a matrix of secondary structure codes, where each row is a residue and each column is a frame.

By default, all protein atoms are considered. The `selection` keyword argument can be used to choose a different selection. The `PDBTools` selection syntax can be used, for example `selection="protein and chain A"`,  or general Julia functions, like `selection=at -> chain(at) in ('A', 'B')`.

The `ss_method` keyword argument can be used to choose the secondary structure prediction method, which can be either `stride_run` or `dssp_run`. The default is `stride_run`. STRIDE is a faster algorithm, while DSSP is the default one in PDB database.

The `show_progress` keyword argument controls whether a progress bar is shown.

For the classes, refer to the ProteinSecondaryStructures.jl package documentation.

## Example

```jldoctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> ssmap = ss_map(simulation; selection="residue >= 30 and residue <= 35", show_progress=false)
6×5 Matrix{Int64}:
 5  9  5  5  5
 5  9  5  5  5
 5  1  5  5  5
 5  1  5  5  5
 5  1  5  5  5
 9  9  9  9  9

julia> ss_name.(ssmap)
6×5 Matrix{String}:
 "turn"  "coil"       "turn"  "turn"  "turn"
 "turn"  "coil"       "turn"  "turn"  "turn"
 "turn"  "310 helix"  "turn"  "turn"  "turn"
 "turn"  "310 helix"  "turn"  "turn"  "turn"
 "turn"  "310 helix"  "turn"  "turn"  "turn"
 "coil"  "coil"       "coil"  "coil"  "coil"

```
