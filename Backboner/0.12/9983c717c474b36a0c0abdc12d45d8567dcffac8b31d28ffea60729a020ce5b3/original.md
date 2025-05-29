```
ChainedBonds{T<:Real,V<:AbstractVector{T}}
```

A lazy way to store a backbone as a series of bond lengths, bond angles, and torsion_angles.

# Examples

```jldoctest
julia> backbone = Backbone(randn(Float32, 3, 660));

julia> bonds = ChainedBonds(backbone)
ChainedBonds{Float32, Vector{Float32}} with 659 bond lengths, 658 bond angles, and 657 torsion angles
```
