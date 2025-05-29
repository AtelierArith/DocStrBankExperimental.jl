```
@generate_basis(s, [export_types, generate_reciprocals, zero_mixed_index])
```

generate types for basis Blades and algebra given a string encoding the desired metric. example metric strings :  "+++" for 3D space "-+++" for minkowski spacetime "0+++" 3D projective space ( homegeneous coords ) 

Optional boolean parameters: export_types -       export the basis types into calling module scope

generate_reciprocals - generate reciprocal basis types with raised indices for all grades

zero*mixed*index -   any operator that results in a blade with mixed dual and primal indices will be set to zero.  You want this true when working with differential k-forms where eᵢ*eʲ = δᵢʲ
