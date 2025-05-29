max_latitude(latitude::Float64, bearing::Float64)

クレアロの公式を使用すると、与えられた `bearing` [deg] と大円上の `latitude` [deg] に基づいて、大円経路の最大緯度 [deg] を計算することができます。

最小緯度は -max_latitude です。

出典: https://www.movable-type.co.uk/scripts/latlong.html
