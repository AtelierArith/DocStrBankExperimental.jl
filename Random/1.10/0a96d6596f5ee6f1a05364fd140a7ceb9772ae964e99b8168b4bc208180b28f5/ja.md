```
rand([rng=default_rng()], [S], [dims...])
```

指定された値の集合 `S` からランダムな要素またはランダムな要素の配列を選択します。`S` は次のいずれかであることができます。

  * インデックス可能なコレクション（例えば `1:9` や `('x', "y", :z)`）、
  * `AbstractDict` または `AbstractSet` オブジェクト、
  * 文字列（文字のコレクションと見なされます）、または
  * 型：選択する値の集合は、整数の場合 `typemin(S):typemax(S)` に相当し（これは [`BigInt`](@ref) には適用されません）、浮動小数点数の場合は $[0, 1)$、複素浮動小数点数の場合は $[0, 1)+i[0, 1)$ になります。

`S` のデフォルトは [`Float64`](@ref) です。オプションの `rng` 以外に1つの引数が渡され、かつそれが `Tuple` の場合、それは値のコレクション（`S`）として解釈され、`dims` とは見なされません。

通常分布の数値については [`randn`](@ref) を、インプレースの同等物については [`rand!`](@ref) および [`randn!`](@ref) を参照してください。

!!! compat "Julia 1.1"
    `S` をタプルとしてサポートするには、少なくとも Julia 1.1 が必要です。


# 例

```julia-repl
julia> rand(Int, 2)
2-element Array{Int64,1}:
 1339893410598768192
 1575814717733606317

julia> using Random

julia> rand(MersenneTwister(0), Dict(1=>2, 3=>4))
1=>2

julia> rand((2, 3))
3

julia> rand(Float64, (2, 3))
2×3 Array{Float64,2}:
 0.999717  0.0143835  0.540787
 0.696556  0.783855   0.938235
```

!!! note
    `rand(rng, s::Union{AbstractDict,AbstractSet})` の複雑さは `s` の長さに対して線形ですが、定数の複雑さを持つ最適化された方法が利用可能な場合（`Dict`、`Set` および密な `BitSet` の場合）、その限りではありません。数回以上呼び出す場合は、代わりに `rand(rng, collect(s))` を使用するか、適切に `rand(rng, Dict(s))` または `rand(rng, Set(s))` を使用してください。

