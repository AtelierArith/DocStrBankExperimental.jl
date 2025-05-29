```julia
approxCliqMarginalUp!(csmc; ...)
approxCliqMarginalUp!(
    csmc,
    childmsgs;
    N,
    dbg,
    multiproc,
    logger,
    iters,
    drawpdf
)

```

近似チャップマン-コルモゴロフ遷移積分を計算し、ベイズ（ジャンクション）ツリーに渡すメッセージとしてセパレーターマージナルを返し、デバッグ用の追加クリーク操作値を提供します。

ノート

  * `onduplicate=true` はデフォルトで内部的にファクターグラフとベイツリーのディープコピーを使用し、与えられたオブジェクトを**更新しません**。計算中に `fgl` と `treel` を更新するには、falseに設定してください。

将来

  * TODO: 内部関数チェーンが長すぎて、保守性のためにリファクタリングが必要です。
