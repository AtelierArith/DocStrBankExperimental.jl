```
struct TriangularLattice <: AbstractLattice{2}
```

2D正方格子を表す型。

三角形パターンでタイルを生成するために[`generate_sites`](@ref)関数の引数として使用され、サイトの繰り返し回数は[`generate_sites`](@ref)の追加引数で指定されます。三角形は2D格子であるため、追加の入力として2つの整数引数が必要です。

# 例

```julia-repl
julia> generate_sites(TriangularLattice(), 3, 3)
9-element AtomList{2, Float64}:
 (0.0, 0.0)
 (1.0, 0.0)
 ...
 (2.0, 1.7320508075688772)
 (3.0, 1.7320508075688772)

```

格子ベクトルとサイトを返すオーバーライドされた関数は[`lattice_vectors(::TriangularLattice)`](@ref)および[`lattice_sites(::TriangularLattice)`](@ref)として存在します。
