```
Scene TODO document this
```

## コンストラクタ

## フィールド

  * `parent`: シーンの親; トップレベルのシーンであれば、`parent == nothing`。
  * `events`: シーンに関連付けられた[`Events`](@ref)。
  * `px_area`: シーンの現在のピクセル面積。
  * `clear`: シーンをクリアする必要があるかどうか。
  * `camera`: シーンに関連付けられた`Camera`。
  * `camera_controls`: シーンのカメラのためのコントロール。
  * `data_limits`: このシーンにプロットされたデータの制限。ユーザーによって設定できず、計算されたデータの境界を保存するためだけに使用される。
  * `transformation`: シーンの[`Transformation`](@ref)。
  * `plots`: シーンに含まれるプロット。
  * `theme`
  * `attributes`
  * `children`: シーンの子はその変換を継承する。
  * `current_screens`: シーンが表示されるスクリーン。
  * `updated`: レイアウトが行われるべきかどうかを示す信号。trueに更新されると、シーンはその属性（`raw`、`center`、または`scale_plot`）に従ってレイアウトされる。
