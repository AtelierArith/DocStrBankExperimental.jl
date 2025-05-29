```
struct SquareLattice <: AbstractLattice{2}
```

2D正方格子を表す型。

[`generate_sites`](@ref)関数の引数として使用され、追加の引数で指定されたサイトの繰り返し回数で正方形のパターンでタイルを生成します。正方形は2D格子であるため、追加の入力として2つの整数引数が必要です。

# 例

```julia-repl
julia> generate_sites(SquareLattice(), 4, 4)
16-element AtomList{2, Float64}:
 (0.0, 0.0)
 (1.0, 0.0)
 ...
 (2.0, 3.0)
 (3.0, 3.0)

```

格子ベクトルとサイトを返すオーバーライドされた関数は、[`lattice_vectors(::SquareLattice)`](@ref)および[`lattice_sites(::SquareLattice)`](@ref)として存在します。
