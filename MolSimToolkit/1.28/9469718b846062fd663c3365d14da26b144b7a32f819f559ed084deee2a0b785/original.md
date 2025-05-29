```
ss_heatmap(ssmap::Matrix{<:Real}; scalex=1.0, kargs...)
```

Plots a heatmap of the secondary structure map. 

!!! note
    This function requires loading the `Plots` package. The `residue_ticks` function   is available in the `PDBTools`` package.


The `scalex` keyword argument can be used to scale the x-axis, which usually has the meaning of time in a simulation. By default, it is 1.0 and the x-axis is the frame number.

The `kargs` keyword arguments are passed to the `heatmap` function of the Plots package, to modify properties of the plot. In particular: 

  * the residue ticks can be set with `yticks`, and can be set to residue specific labels with the `residue_ticks` function of PDBTools.
  * the x-axis label can be set with `xlabel` to appropriate units, such as "time / ns", in combination with `scalex`.

## Example

```julia-repl
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> using Plots, PDBTools

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> ssmap = ss_map(simulation; ss_method=stride_run, show_progress=false);

julia> protein = select(atoms(simulation), "protein");

julia> ss_heatmap(ssmap; scalex=0.1, xlabel="time / ns", yticks=residue_ticks(prot; stride=5))
```

Will plot a heatmap of the secondary structure map, with the x-axis scaled to 0.1, and residue ticks every 5 residues. The plot can be saved with the `savefig` function of the Plots package.
