インタラクティブな地図を作成して、場所を選択します。

Plutoノートブックでの基本的な使用法：

```julia
@bind place MapPicker(0.0, 0.0, 1)
```

地図を描画するために[Leaflet](https://leafletjs.com/)を使用します。デフォルトでは、地図はOpenStreetMapのタイルを使用します。OSMの[使用ポリシー](https://operations.osmfoundation.org/policies/tiles/)をお読みください。

ユーザーは地図上にマーカーを置いて場所を選択できます。Plutoで`@bind`を使用すると、バウンド変数は`"lat"`と`"lng"`というキーを持つ`Dict`で座標を受け取ります。マーカーが置かれていない場合は`nothing`が返されます。

入力：

地図が最初に中心を合わせるべき緯度と経度、および初期ズームレベルを指定する必要があります。

追加のパラメータ：

  * `tile_layer`: `TileLayer`の設定。
  * `height`: 地図の高さ（ピクセル単位）。
