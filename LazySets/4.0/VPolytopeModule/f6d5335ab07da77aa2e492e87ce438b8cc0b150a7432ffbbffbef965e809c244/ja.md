# 拡張ヘルプ

```
rand(::Type{VPolytope}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing,
     [num_vertices]::Int=-1)
```

### 入力

  * `num_vertices` – （オプション、デフォルト: `-1`）多面体の頂点の数の上限（下記のコメントを参照）

### アルゴリズム

すべての数値は平均0、標準偏差1の正規分布に従います。

頂点の数は引数`num_vertices`で制御できます。負の値の場合、範囲`dim:5*dim`の中からランダムな数を選択します（ただし、`dim == 1`の場合は範囲`1:2`の中から選択します）。

この実装は、頂点が冗長でないことを保証しないため、結果として`num_vertices`で指定された数よりも少ない頂点が得られる場合があります。
