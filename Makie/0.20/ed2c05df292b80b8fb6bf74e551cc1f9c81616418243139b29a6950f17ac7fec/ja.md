```
シーン TODO ドキュメント
```

## コンストラクタ

## フィールド

  * `parent`: シーンの親; トップレベルのシーンの場合、`parent == nothing`。
  * `events`: シーンに関連付けられた[`Events`](@ref)。
  * `viewport`: シーンの現在のピクセル領域。
  * `clear`: シーンをクリアする必要があるかどうか。
  * `camera`: シーンに関連付けられた`Camera`。
  * `camera_controls`: シーンのカメラのためのコントロール。
  * `transformation`: シーンの[`Transformation`](@ref)。
  * `plots`: シーンに含まれるプロット。
  * `theme`
  * `children`: シーンの子はその変換を継承する。
  * `current_screens`: シーンが表示されるスクリーン。
  * `backgroundcolor`
  * `visible`
  * `ssao`
  * `lights`
  * `deregister_callbacks`
  * `cycler`
