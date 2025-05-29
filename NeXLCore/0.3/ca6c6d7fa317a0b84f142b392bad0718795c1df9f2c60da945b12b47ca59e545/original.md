```
asoxide(elms::Pair{Element, <:AbstractFloat}...; valences = NeXLCore.defaultValences, atomicweights::Dict{Element,<:AbstractFloat} = Dict{Element,Float64}())
asoxide(elms::Dict{Element, <:AbstractFloat}...; valences = NeXLCore.defaultValences, atomicweights::Dict{Element,<:AbstractFloat} = Dict{Element,Float64}())
```

Providing the mass-fraction of the consituent elements in `elms`, compute the corresponding amounts of the oxide forms of the elements.  This can be used to answer the question: If I measure this amount of these elements, what mass fraction of the oxide-forms of each element does this correspond to?  The example below demonstrates that Albite is 68.74% SiO₂ by mass. By default, `val = NeXLCore.valences`, a typical set of valences.  See also `obystoichiometry(...)`

Example:

```
julia> mat"NaAlSi3O8"
  NaAlSi3O8[Al=0.1029,Na=0.0877,Si=0.3213,O=0.4881]
julia> asoxide(n"Al"=>0.1029, n"Na"=>0.0877, n"Si"=>0.3213)
  Dict{Material, Float64} with 3 entries:
  SiO₂[O=0.5326,Si=0.4674]  => 0.687366
  Al₂O₃[Al=0.5293,O=0.4707] => 0.194424
  Na₂O[Na=0.7419,O=0.2581]  => 0.118216
julia> sum(asoxide(n"Al"=>0.1029, n"Na"=>0.0877, n"Si"=>0.3213), name="Albite")
  Albite[Al=0.1029,Na=0.0877,O=0.4881,Si=0.3213]
julia> asoxide(filter(kv->kv[1]!=n"O", massfraction(mat"NaAlSi3O8")))
  Dict{Material, Float64} with 3 entries:
    SiO₂[O=0.5326,Si=0.4674]  => 0.687401
    Al₂O₃[Al=0.5293,O=0.4707] => 0.194418
    Na₂O[Na=0.7419,O=0.2581]  => 0.118181
```
