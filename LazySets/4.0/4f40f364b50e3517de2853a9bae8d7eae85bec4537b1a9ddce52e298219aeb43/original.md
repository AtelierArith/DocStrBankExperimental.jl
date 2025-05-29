```
reduce_order(Z::AbstractZonotope, r::Real,
             [method]::AbstractReductionMethod=GIR05())
```

Reduce the order of a zonotopic set by overapproximating with a zonotope with fewer generators.

### Input

  * `Z`      – zonotopic set
  * `r`      – desired order
  * `method` – (optional, default: `GIR05()`) the reduction method used

### Output

A new zonotope with fewer generators, if possible.

### Algorithm

The available algorithms are:

```jldoctest; setup = :(using LazySets: subtypes, AbstractReductionMethod)
julia> subtypes(AbstractReductionMethod)
3-element Vector{Any}:
 LazySets.ASB10
 LazySets.COMB03
 LazySets.GIR05
```

See the documentation of each algorithm for references. These methods split the given zonotopic set `Z` into two zonotopes, `K` and `L`, where `K` contains the most "representative" generators and `L` contains the generators that are reduced, `Lred`, using a box overapproximation. We follow the notation from [YangS18](@citet). See also [KopetzkiSA17](@citet).
