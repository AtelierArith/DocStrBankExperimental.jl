```
randatom(
    [rng::Union{Random.AbstractRNG,Integer},]
    a::UnionAlphabet;
    atompicking_mode::Symbol=:uniform,
    subalphabets_weights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}=nothing
)::Atom
```

`UnionAlphabet`から原子をサンプリングします。デフォルトでは、サンプリングは原子に対して均一です。

`atompicking_mode = :uniform_subalphabets`を設定することで、サブアルファベットに対して均一なサンプリングを強制することができます。

さらに、`subalphabets_weights`ベクトルとともに`:weighted`の`atompicking_mode`を指定することもできます。

# 例

```julia-repl
julia> alphabet1 = ExplicitAlphabet(Atom.(1:10));
julia> alphabet2 = ExplicitAlphabet(Atom.(11:20));
julia> union_alphabet = UnionAlphabet([alphabet1, alphabet2]);

julia> randatom(42, union_alphabet)
Atom{Int64}: 11

julia> randatom(42, union_alphabet; atompicking_mode=:uniform_subalphabets)
Atom{Int64}: 11

julia> for i in 1:10
            randatom(
                union_alphabet;
                atompicking_mode=:weighted,
                subalphabets_weights=[0.8,0.2]
            ) |> syntaxstring |> vcat |> print
        end
["6"]["3"]["10"]["7"]["2"]["2"]["6"]["9"]["20"]["16"]
```

[`UnionAlphabet`](@ref)も参照してください。
