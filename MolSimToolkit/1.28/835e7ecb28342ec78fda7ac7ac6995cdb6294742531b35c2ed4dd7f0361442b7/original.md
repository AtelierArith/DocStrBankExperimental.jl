```
ss_mean(ssmap::AbstractMatrix{<:Integer}; class, dims=nothing)
```

Calculates the mean secondary structure class content of the trajectory, given the secondary structure map.

The secondary structure class to be considered must be defined by the `class` keyword argument.

`class` can be either a string, a character, or an integer, or a set of values, setting the class(es)  of secondary structure to be consdiered. For example, for `alpha helix`, use "H". It can also be a vector of classes,  such as `class=["H", "E"]`.

The mean can be calculated along the residues (default) or along the frames, by setting the `dims` keyword argument.

  * `dims=nothing` (default) calculates the mean occurence of `ss_class` of the whole matrix.
  * `dims=1` calculates the mean occurence of `ss_class` along the frames, for each residue.
  * `dims=2` calculates the mean occurence of `ss_class` along the residues, for each frame.

The classes can be found in the ProteinSecondaryStructures.jl package documentation.

## Example

```jldoctest ;filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> ssmap = ss_map(simulation; # 5 frames 
                   selection="residue >= 30 and residue <= 35", # 6 residues
                   show_progress=false
               );

julia> ss_mean(ssmap; class="C")
0.23333333333333334

julia> ss_mean(ssmap; class="C", dims=1) # mean coil content per residue
5-element Vector{Float64}:
 0.16666666666666666
 0.5
 0.16666666666666666
 0.16666666666666666
 0.16666666666666666 

julia> ss_mean(ssmap; class="C", dims=2) # mean coil content per frame
6-element Vector{Float64}:
 0.2
 0.2
 0.0
 0.0
 0.0
 1.0

julia> ss_mean(ssmap; class=["C", "T"]) # mean coil or turn
0.9

```
