```
sc, vfG, vfC = example_torsion_chaos(n::Int, p::Int)
```

1次元のトーションを持つ空間の三角形分割を作成し、この複体上に2つのフォーマンベクトル場を定義します。

この関数は、以下の整数ホモロジー群を持つ単体複体 `sc` を返します：

  * 次元0では整数の群です。
  * 次元1では `n` に対する整数の剰余です。
  * 次元2では自明な群です。

言い換えれば、この単体複体は次元1に非自明なトーションを持っています。これは、すべての境界辺が反時計回りに向けられ、これらの辺がすべて同一視される `n`-角形の三角形分割です。パラメータ `p` は基礎となる体の特性を指定します。

さらに、2つのフォーマンベクトル場 `vfG` と `vfC` が返されます。最初のものは、接続行列に大きな接続行列のエントリを持つ勾配ベクトル場です。実際、`p` が `n` より大きい任意の素数であれば、行列に `n` のエントリがあります。2番目のフォーマンベクトル場は、カオス的なモース集合を含みます。このモース集合は、ほとんどの `p` に対して自明なモース指数を持ちます。一方、素数 `p = n` の場合、この集合は不安定な周期軌道のモース指数を持ちます。

# 例

```jldoctest
julia> sc, vfG, vfC = example_torsion_chaos(3,7);

julia> homology(sc)
3-element Vector{Int64}:
 1
 0
 0

julia> cmG = connection_matrix(sc, vfG);

julia> sparse_show(cmG.matrix)
[0   0   0]
[0   0   3]
[0   0   0]

julia> print(cmG.labels)
["0w", "0w0x", "0w0x1s"]

julia> cmC = connection_matrix(sc, vfC);

julia> sparse_show(cmC.matrix)
[0]

julia> print(cmC.labels)
["0w"]

julia> msC, psC = morse_sets(sc, vfC, poset=true);

julia> [conley_index(sc, mset) for mset in msC]
2-element Vector{Vector{Int64}}:
 [1, 0, 0]
 [0, 0, 0]

julia> psC
2×2 Matrix{Bool}:
 0  1
 0  0

julia> length.(msC)
2-element Vector{Int64}:
  1
 26
```
