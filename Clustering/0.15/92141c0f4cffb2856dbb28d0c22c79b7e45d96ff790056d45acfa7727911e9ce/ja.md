```
varinfo(a, b) -> Float64
```

同じデータポイントの2つのクラスタリング間の*情報の変動*を計算します。

`a`と`b`は、[`ClusteringResult`](@ref) インスタンスまたは割り当てベクトル（`AbstractVector{<:Integer}`）のいずれかです。

# 参考文献

> Meila, Marina (2003). *情報の変動によるクラスタリングの比較.* 学習理論とカーネルマシン: 173–187.

