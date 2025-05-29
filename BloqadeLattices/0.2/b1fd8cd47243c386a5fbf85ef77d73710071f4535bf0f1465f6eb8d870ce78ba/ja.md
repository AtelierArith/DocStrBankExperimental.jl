```
struct ChainLattice <: AbstractLattice{1}
```

1Dチェーン格子を表す型。

[`generate_sites`](@ref)関数の引数として使用され、追加の引数で指定されたサイトの繰り返し回数でチェーンパターンのタイルを生成します。チェーンは1D格子であるため、追加の入力として1つの整数引数が必要です。

# 例

```julia-repl
julia> generate_sites(ChainLattice(), 5)
5-element AtomList{1, Float64}:
 (0.0,)
 (1.0,)
 (2.0,)
 (3.0,)
 (4.0,)
```

格子ベクトルとサイトを返すオーバーライドされた関数は、[`lattice_vectors(::ChainLattice)`](@ref)および[`lattice_sites(::ChainLattice)`](@ref)として存在します。
