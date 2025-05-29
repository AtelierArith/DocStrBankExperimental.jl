```
randatom(
    [rng::Union{Random.AbstractRNG,Integer},]
    a::AbstractAlphabet,
    args...;
    kwargs...
)
```

*有限* [`AbstractAlphabet`](@ref) から一様分布に従って [`Atom`](@ref) をランダムに生成します。

# 例

```julia-repl
julia> alphabet = ExplicitAlphabet(1:5)
ExplicitAlphabet{Int64}(Atom{Int64}[Atom{Int64}: 1, Atom{Int64}: 2, Atom{Int64}: 3, Atom{Int64}: 4, Atom{Int64}: 5])

julia> randatom(42, alphabet)
Atom{Int64}: 4
```

他に [`natoms`](@ref)、[`AbstractAlphabet`](@ref) も参照してください。
