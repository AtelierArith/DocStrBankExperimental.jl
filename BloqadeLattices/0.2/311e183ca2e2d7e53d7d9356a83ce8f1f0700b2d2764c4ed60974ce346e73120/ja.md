```
struct KagomeLattice <: AbstractLattice{2}
```

2D Kagome格子を表す型。

[`generate_sites`](@ref) 関数の引数として使用され、Kagomeパターンでのタイルを生成します。サイトの繰り返し回数は、[`generate_sites`](@ref) の追加引数によって指定されます。Kagomeは2D格子であるため、追加の入力として2つの整数引数が必要です。

# 例

```julia-repl
julia> generate_sites(KagomeLattice(), 3, 3)
27-element AtomList{2, Float64}:
 (0.0, 0.0)
 (0.25, 0.4330127018922193)
 ...
 (3.25, 2.1650635094610964)
 (3.75, 2.1650635094610964)
```

格子ベクトルとサイトを返すオーバーライドされた関数は、[`lattice_vectors(::KagomeLattice)`](@ref) および [`lattice_sites(::KagomeLattice)`](@ref) として存在します。
