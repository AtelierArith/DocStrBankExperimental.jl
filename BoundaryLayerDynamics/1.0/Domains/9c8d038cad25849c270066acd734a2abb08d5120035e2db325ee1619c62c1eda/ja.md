```
SinusoidalMapping(η, variant = :auto)
```

次の形式のマッピングを使用して変換された垂直座標を定義します。

$$
x_3 = \frac{\sin(ζ η π/2)}{\sin(η π/2)}
$$

範囲 $0≤ζ≤1$ を [`Domain`](@ref) の $x_3$ 範囲にマッピングするように適切に再スケーリングします。

パラメータ $0<η<1$ はグリッドの引き伸ばしの強さを制御し、$0$ に近い値はより等間隔の間隔をもたらし、$1$ に近い値は壁に近いグリッド点の密度を高めます。値 $η=1$ は、壁でのマッピング関数の導関数が消失するため許可されていません。

`variant` は、座標がどの境界で洗練されるかを定義し、`:below`、`:above`、`:symmetric`（両方の境界が洗練される）、または `:auto`（境界層を生成する境界のために洗練される）に設定できます。
