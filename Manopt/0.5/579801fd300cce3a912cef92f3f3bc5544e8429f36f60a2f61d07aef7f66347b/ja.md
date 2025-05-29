```
DebugPrimalDualResidual <: DebugAction
```

プライマルデュアル残差を印刷するためのデバッグアクションです。コンストラクタは印刷関数といくつかの（共有）ストレージを受け入れ、少なくとも `:Iterate`、`:X`、および `:n` を記録する必要があります。

# コンストラクタ

```
DebugPrimalDualResidual()
```

キーワード付き引数を使用して

# キーワード付き引数

  * `io=`stdout`: デバッグを実行するストリーム
  * `format="$prefix%s"`: デュアル残差を印刷するためのフォーマット
  * `prefix="PD Residual: "`: プレフィックスを設定するための短い形式
  * `storage`（デバッグ用の値を保存するための新しい [`StoreStateAction`](@ref)）
