```julia
littlegroup(
    sg::Crystalline.SpaceGroup,
    kv::Crystalline.KVec
) -> Crystalline.LittleGroup
littlegroup(
    sg::Crystalline.SpaceGroup,
    kv::Crystalline.KVec,
    klab::String
) -> Crystalline.LittleGroup

```

Return the little group associated with space group `sg` at the **k**-vector `kv`.

Optionally, an associated **k**-vector label `klab` can be provided; if not provided, the empty string is used as label.
