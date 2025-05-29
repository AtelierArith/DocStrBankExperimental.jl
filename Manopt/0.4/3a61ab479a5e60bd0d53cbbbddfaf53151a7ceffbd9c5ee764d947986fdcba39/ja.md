```
DebugPrimalResidual <: DebugAction
```

プライマル残差を印刷するためのデバッグアクション。コンストラクタは印刷関数といくつかの（共有）ストレージを受け入れ、少なくとも `:Iterate`、`:X`、および `:n` を記録する必要があります。

# コンストラクタ

```
DebugPrimalResidual()
```

キーワードは次のとおりです。

  * `io` (`stdout`) - デバッグを実行するストリーム
  * format (`"$prefix%s"`) デュアル残差を印刷するためのフォーマット
  * `prefix` (`"Primal Residual: "`) プレフィックスを設定するための短い形式
  * `storage` (新しい [`StoreStateAction`](@ref)) デバッグ用の値を保存するためのもの。
