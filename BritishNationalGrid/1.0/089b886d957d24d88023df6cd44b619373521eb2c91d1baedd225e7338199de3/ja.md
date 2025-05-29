```
gridref(p::BNGPoint, n; square=false, sep=' ')
```

`n`桁のグリッド参照を返す文字列を生成します。デフォルトでは、完全な参照が提供されます。`square`が`true`の場合、最初に100 kmの正方形の名前を提供し、その後にその正方形内の参照を提供します。正方形、東座標、北座標は`sep`で区切られます。

```jldoctest
julia> gridref(BNGPoint(429157, 623009), 8, square=true, sep="_")
"NU_2915_2300"

```
