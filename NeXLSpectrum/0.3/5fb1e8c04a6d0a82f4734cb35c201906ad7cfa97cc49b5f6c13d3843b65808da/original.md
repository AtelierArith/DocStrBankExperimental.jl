```
reference( elm::Element, spec::Spectrum, mat::Material=spec[:Composition]; pc = nothing, lt = nothing, e0 = nothing, coating = nothing)::ReferencePacket
reference(els::AbstractVector{Element}, spec::Spectrum, mat::Material = spec[:Composition]; pc = nothing, lt = nothing, e0 = nothing, coating = nothing)::Vector{ReferencePacket}
```

Construct a `ReferencePacket` from a `Spectrum` collected from the specified `Material` for the specified `Element`. Often used with `references(...)` to build `FilterFitPacket`s.

Optional named arguments `pc`, `lt`, `e0`, `coating` allow you to specify the probe current, live time, beam energy and sample coating.
