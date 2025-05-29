```
struct HoneycombLattice <: AbstractLattice{2}
```

2Dハニカム格子を表す型。

[`generate_sites`](@ref)関数の引数として使用され、ハニカムパターンでのタイルを生成します。サイトの繰り返し回数は、[`generate_sites`](@ref)の追加引数によって指定されます。ハニカムは2D格子であるため、追加の入力として2つの整数引数が必要です。

# 例

```julia-repl
julia> generate_sites(HoneycombLattice(), 5, 5)
50-element AtomList{2, Float64}:
 (0.0, 0.0)
 (0.5, 0.2886751345948129)
...
 (6.0, 3.4641016151377544)
 (6.5, 3.7527767497325675)

```

格子ベクトルとサイトを返すオーバーライドされた関数は、[`lattice_vectors(::HoneycombLattice)`](@ref)および[`lattice_sites(::HoneycombLattice)`](@ref)として存在します。
