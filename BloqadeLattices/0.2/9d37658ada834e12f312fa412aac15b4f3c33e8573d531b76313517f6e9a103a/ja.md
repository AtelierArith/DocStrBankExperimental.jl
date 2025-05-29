```
struct LiebLattice <: AbstractLattice{2}
```

2D Lieb Latticeを表す型です。

[`generate_sites`](@ref)関数の引数として使用され、追加の引数で指定されたサイトの繰り返し回数を持つLieb（正方形が減少した）パターンでタイルを生成します。Liebは2D格子であるため、追加の入力として2つの整数引数が必要です。

# 例

```julia-repl
julia> generate_sites(LiebLattice(), 3, 3)
27-element AtomList{2, Float64}:
 (0.0, 0.0)
 (0.5, 0.0)
...
 (2.5, 2.0)
 (2.0, 2.5)
```

格子ベクトルとサイトを返すオーバーライドされた関数は、[`lattice_vectors(::LiebLattice)`](@ref)および[`lattice_sites(::LiebLattice)`](@ref)として存在します。
