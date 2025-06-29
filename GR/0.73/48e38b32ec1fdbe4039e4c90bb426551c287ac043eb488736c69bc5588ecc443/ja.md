```
axes2d(x_tick::Real, y_tick::Real, x_org::Real, y_org::Real, major_x::Int, major_y::Int, tick_size::Real)
```

X軸とY軸を線形および/または対数的に間隔を空けた目盛りで描画します。

**パラメータ:**

`x_tick`, `y_tick` :     各軸のマイナー目盛り間の間隔。 `x_org`, `y_org` :     X軸とY軸の交点の原点のワールド座標。 `major_x`, `major_y` :     メジャー目盛り間のマイナー目盛り間隔の数を指定する単位のない整数値。 0または1の値はマイナー目盛りがないことを意味します。 負の値は、関連する軸にラベルが描画されないことを指定します。 `tick_size` :     正規化デバイス座標単位で指定されたマイナー目盛りの長さ。 メジャー目盛りはマイナー目盛りの2倍の長さです。 負の値は、目盛りを内向きから外向き（またはその逆）に反転させます。

目盛りは各軸に沿って配置され、メジャー目盛りは軸の原点に落ちるように配置されます（表示されているかどうかにかかわらず）。 メジャー目盛りには対応するデータ値がラベル付けされます。 軸はウィンドウのスケールに従って描画されます。 軸と目盛りは実線を使用して描画され、線の色と幅は`setlinetype`および`setlinewidth`関数を使用して変更できます。 軸は`setscale`関数によって確立された線形または対数変換に従って描画されます。
