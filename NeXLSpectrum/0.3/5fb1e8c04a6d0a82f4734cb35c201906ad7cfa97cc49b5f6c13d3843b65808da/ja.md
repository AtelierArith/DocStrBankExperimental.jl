```
reference( elm::Element, spec::Spectrum, mat::Material=spec[:Composition]; pc = nothing, lt = nothing, e0 = nothing, coating = nothing)::ReferencePacket
reference(els::AbstractVector{Element}, spec::Spectrum, mat::Material = spec[:Composition]; pc = nothing, lt = nothing, e0 = nothing, coating = nothing)::Vector{ReferencePacket}
```

指定された`Element`のために指定された`Material`から収集された`Spectrum`から`ReferencePacket`を構築します。通常、`references(...)`と共に使用され、`FilterFitPacket`を構築します。

オプションの名前付き引数`pc`、`lt`、`e0`、`coating`を使用すると、プローブ電流、ライブタイム、ビームエネルギー、およびサンプルコーティングを指定できます。
