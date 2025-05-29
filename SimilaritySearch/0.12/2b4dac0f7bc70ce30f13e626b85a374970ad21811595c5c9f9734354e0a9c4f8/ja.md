```
closestpair(idx::AbstractSearchIndex, ctx::AbstractContext; minbatch=0)
```

`idx`内のすべての要素の中から最も近いペアを見つけます。インデックス`idx`が近似である場合、点のペアも近似である可能性があります。

# 引数:

  * `idx`: 点の集合をインデックスする検索構造
  * `ctx`: 検索コンテキスト（キャッシュ、ハイパーパラメータなど）

# キーワード引数:

  * `minbatch`: 構成の評価にマルチスレッドがどのように使用されるかを制御します。[`getminbatch`](@ref)を参照してください。
