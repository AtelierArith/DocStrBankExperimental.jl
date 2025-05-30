```
initial(::Type{UnravelledInitialLayout}, N::T) where {T <: EcologicalNetworks.AbstractUnipartiteNetwork}
```

Unravelled disposition of nodes on trophic levels for food webs, where the x axis is the omnivory index. Note that the *fractional* trophic level is used, but the layout can be modified afterwards to use the continuous levels. See the documentation for `UnravelledLayout` to see how.
