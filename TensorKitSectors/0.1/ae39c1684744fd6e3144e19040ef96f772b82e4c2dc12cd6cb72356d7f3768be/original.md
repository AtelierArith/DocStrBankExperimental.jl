```
FusionStyle(::Sector)
FusionStyle(I::Type{<:Sector})
```

Trait to describe the fusion behavior of sectors of type `I`, which can be either

  * `UniqueFusion()`: single fusion output when fusing two sectors;
  * `SimpleFusion()`: multiple outputs, but every output occurs at most one,   also known as multiplicity-free (e.g. irreps of $SU(2)$);
  * `GenericFusion()`: multiple outputs that can occur more than once (e.g. irreps   of $SU(3)$).

There is an abstract supertype `MultipleFusion` of which both `SimpleFusion` and `GenericFusion` are subtypes. Furthermore, there is a type alias `MultiplicityFreeFusion` for those fusion types which do not require muliplicity labels, i.e. `MultiplicityFreeFusion = Union{UniqueFusion,SimpleFusion}`.
