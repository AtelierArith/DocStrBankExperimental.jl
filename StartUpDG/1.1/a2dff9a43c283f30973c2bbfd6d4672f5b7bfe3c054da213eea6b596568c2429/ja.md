```
`PhysicalFrame{NDIMS} <: AbstractElemShape{NDIMS}`
```

`PhysicalFrame`要素タイプ。全体次数Nの近似空間を使用しますが、三角形PKDO基底ではなく、テンソル積レジェンドル基底で計算されます。物理座標をシフト/スケールして参照要素上に配置するためのフィールド`shifting`と`scaling`を格納します。

```
PhysicalFrame()
PhysicalFrame(x, y)
PhysicalFrame(x, y, vx, vy): 背景の直交セルの座標`vx, vy`を格納します
```

PhysicalFrameオブジェクトのコンストラクタ（オプションでカット要素上の点の配列`x`、`y`を使用します）。
