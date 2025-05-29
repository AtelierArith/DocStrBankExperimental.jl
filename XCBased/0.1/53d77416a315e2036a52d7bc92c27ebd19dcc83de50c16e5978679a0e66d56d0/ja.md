```
XCBScreen
```

Xスクリーンに関するデータ。この構造体には以下のフィールドがあります：

  * `root` – スクリーンのルートウィンドウ
  * `default_colormap` – スクリーンのデフォルトカラーマップ
  * `white_pixel` – スクリーンの白いピクセル値
  * `black_pixel` – スクリーンの黒いピクセル値
  * `current_input_masks` – スクリーンの現在の入力マスクのビットマスク
  * `width_in_pixels` – ピクセル単位のスクリーン幅
  * `height_in_pixels` – ピクセル単位のスクリーン高さ
  * `width_in_millimeters` – ミリメートル単位のスクリーン幅
  * `height_in_millimeters` – ミリメートル単位のスクリーン高さ
  * `min_installed_maps` – 同時にインストールされることが保証されるマップの数（各マップに割り当てられたエントリの数に関係なく）
  * `max_installed_maps` – 割り当てに応じて同時にインストールされる可能性のあるマップの最大数
  * `root_visual` – スクリーンのルートウィンドウのビジュアル
  * `backing_stores` – サーバーがこのスクリーンのためにバックストレージをサポートしているかどうかを示します（`XCB_BACKING_STORE_NOT_USEFUL`、`XCB_BACKING_STORE_WHEN_MAPPED`、および `XCB_BACKING_STORE_ALWAYS` のいずれか）
  * `save_unders` – サーバーがCreateWindowおよびChangeWindowAttributesでセーブアンダーモードをサポートできるかどうか
  * `root_depth` – スクリーンのルートウィンドウの深さ
  * `allowed_depths` – 許可された深さをその[`XCBVisualType`](@ref)にマッピングする`Dict`。
