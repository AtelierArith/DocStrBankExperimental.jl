# ribbon_graph

```julia
ribbon_graph(amat; m, c)

```

周辺化と条件付けの後のリボングラフ。

### 必要な引数

```julia
* `amat::NamedArray{Int, 2}`           : DAGの隣接行列
```

### オプションの引数

```julia
* `m::Vector{Symbol}`                  : 周辺化されるDAGのノード
* `c::Vector{Symbol})`                 : 条件付けされるDAGのノード
```

### 戻り値

```julia
* `rg::NamedArray`                     : 残りのリボングラフ
```

# 拡張ヘルプ

### 例

### ggmでのテストに使用される隣接行列

```julia
amat_data = transpose(reshape([
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,
  0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,
  0,0,0,0,1,0,1,0,1,1,0,0,0,0,0,0,
  1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  1,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,
  0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0
], (16,16)));

vars = [Symbol("n\$i") for i in 1:size(amat_data, 1)]
amat = NamedArray(Int.(amat_data), (vars, vars), ("Rows", "Cols"));
m = [:n3, :n5, :n6, :n15, :n16];
c = [:n4, :n7];

rg = ribbon_graph(amat; m = m, c = c)
```

### 謝辞

原著者:                       Kayvan Sadeghi

Juliaへの翻訳:                   Rob J Goedman

### 参考文献

Sadeghi, K. (2011). Directed acyclic graphsを含む安定グラフのクラス。

Richardson, T.S. and Spirtes, P. (2002).  Ancestral graph Markov models {Annals of Statistics}, 30(4), 962-1030.

Sadeghi, K. and Lauritzen, S.L. (2011). [ループのない混合グラフのマルコフ特性](http://arxiv.org/abs/1109.5909)。

### ライセンス

Rパッケージggmはライセンス: GPL-2の下でライセンスされています。

Juliaの翻訳は: MITの下でライセンスされています。

APIの一部、エクスポートされています。
