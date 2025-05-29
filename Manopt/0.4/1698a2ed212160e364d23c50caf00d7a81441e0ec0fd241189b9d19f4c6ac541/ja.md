```
DebugDualResidual <: DebugAction
```

デバッグアクションで、デュアル残差を印刷します。コンストラクタは印刷関数といくつかの（共有）ストレージを受け入れ、少なくとも `:Iterate`、`:X`、および `:n` を記録する必要があります。

# コンストラクタ

DebugDualResidual()

キーワードを使用して

  * `io` (`stdout`) - デバッグを実行するストリーム
  * format (`"$prefix%s"`) デュアル残差を印刷するためのフォーマット
  * `prefix` (`"Dual Residual: "`) プレフィックスを設定するための短い形式
  * `storage` (新しい [`StoreStateAction`](@ref)) デバッグ用の値を保存するためのもの。
