```
construct(ys::T, Xs::T) where {T<:Tuple{NamedMatrix,NamedMatrix}}
```

*de novo* ネットワークベースの推論予測のためのクエリ-フィーチャー-ソース-ターゲットネットワークを構築し、隣接行列を返します。

# 引数

  * `dts::Tuple{NamedMatrix,NamedMatrix}` : ソース-ターゲット二部グラフの隣接行列
  * `dfs::Tuple{NamedMatrix,NamedMatrix}` : ソース-フィーチャー二部グラフの隣接行列

# 拡張ヘルプ

この実装は、時間分割交差検証またはクエリネットワークの手動構築を目的としています。
