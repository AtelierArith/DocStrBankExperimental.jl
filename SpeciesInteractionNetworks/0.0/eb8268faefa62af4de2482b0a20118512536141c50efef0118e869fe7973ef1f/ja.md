```
spectralradius(N::SpeciesInteractionNetwork{<:Bipartite, <:Binary}; kwargs...)
```

二部グラフ版の [`spectralradius`](@ref) は、まず二部ネットワークを [`render`](@ref) を使用して一部ネットワークとして投影することによって測定されます。その後、一部版と同じオプションが適用されます。
