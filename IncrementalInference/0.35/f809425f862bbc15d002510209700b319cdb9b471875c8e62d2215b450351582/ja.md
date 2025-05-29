```julia
rebuildFactorMetadata!(dfg, factor; ...)
rebuildFactorMetadata!(
    dfg,
    factor,
    neighbors;
    _blockRecursionGradients
)

```

packedTypeをデシリアライズした後、これを使用して因子のCCWとユーザーデータを完全に再構築します。

ノート:

  * この関数は、キャッシュが重い因子、例えば`ObjectAffordanceSubcloud`に使用される可能性があります。

開発ノート:

  * TODO: 本当にこれをメモリ内で行うべきかどうかを確認する必要があります（これをレビューしてください）。
  * TODO: テストが必要です。
