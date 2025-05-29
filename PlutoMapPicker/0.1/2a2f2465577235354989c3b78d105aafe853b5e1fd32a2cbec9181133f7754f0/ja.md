複数の場所を選択するためのインタラクティブマップを作成します

Plutoノートブックでの基本的な使用法：

```julia
@bind places MapPickerMultiple(0.0, 0.0, 1)
```

[Leaflet](https://leafletjs.com/)を使用してマップをレンダリングします。デフォルトでは、マップはOpenStreetMapのタイルを使用します。OSMの[使用ポリシー](https://operations.osmfoundation.org/policies/tiles/)をお読みください。

ユーザーはマップ上にマーカーを配置したり削除したりして場所を選択できます。Plutoで`@bind`を使用すると、バインドされた変数は選択された各ポイントの座標を含む配列を受け取ります。各ポイントは、キー `"lat"` と `"lng"` を持つ `Dict` として提供されます。

入力：

マップが最初に中心を合わせるべき緯度と経度、および初期ズームレベルを指定する必要があります。

追加のパラメータ：

  * `tile_layer`: `TileLayer`の設定。
  * `height`: マップの高さ（ピクセル単位）。
