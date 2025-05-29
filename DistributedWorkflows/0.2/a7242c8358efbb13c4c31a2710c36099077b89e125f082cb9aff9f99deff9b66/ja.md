```
connect(pnet::Workflow_PetriNet, place_port::Vector{Tuple{Place, Symbol}})
connect(pnet::Workflow_PetriNet, port_place::Vector{Tuple{Symbol, Place}})
```

与えられたペトリネットに対して、指定されたプレースをポート名port*nameおよびポートタイプport*typeに接続します。

参照：[`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`remove`](@ref).
