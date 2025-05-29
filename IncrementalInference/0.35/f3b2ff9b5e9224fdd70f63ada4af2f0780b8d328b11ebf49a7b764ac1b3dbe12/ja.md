```julia
resetTreeCliquesForUpSolve!(treel)

```

ベイズ（ジャンクション）ツリーをリセットして、新しいアップソルブを実行できるようにします。

ノート

  * 以前のクリークのステータスを `DOWNSOLVED` から `INITIALIZED` のみに変更します。
  * ツリークリークの色を `lightgreen` に設定します。
