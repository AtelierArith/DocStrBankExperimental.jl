```
DebugPrimalResidual <: DebugAction
```

プライマル残差を印刷するためのデバッグアクションです。コンストラクタは印刷関数といくつかの（共有）ストレージを受け入れ、少なくとも `:Iterate`、`:X`、および `:n` を記録する必要があります。

# コンストラクタ

```
DebugPrimalResidual(; kwargs...)
```

# キーワード引数

  * `io=`stdout`: デバッグを行うストリーム
  * `format="$prefix%s"`: デュアル残差を印刷するためのフォーマット
  * `prefix="Primal Residual: "`: プレフィックスを設定するための短い形式
  * `storage`（デバッグ用の値を保存するための新しい [`StoreStateAction`](@ref)）
