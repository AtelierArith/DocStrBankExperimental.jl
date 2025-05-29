```
T10block(
    Length::T,
    Width::T,
    Height::T,
    nL::IT,
    nW::IT,
    nH::IT;
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

Generate a tetrahedral  mesh of T10 elements  of a rectangular block.
