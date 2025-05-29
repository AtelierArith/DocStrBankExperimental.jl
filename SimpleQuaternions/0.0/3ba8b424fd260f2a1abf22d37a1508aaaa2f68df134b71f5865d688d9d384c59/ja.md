`SimpleQuaternion` はクォータニオン数を作成します。基本コンストラクタは `SimpleQuaternion(a,b,c,d)` で、これは `a + b*im + c*jm + d*km` に相当します。

`SimpleQuaternion(x::Real)` は `x + 0*im + 0*jm + 0*km` を返します。

もし `z` が `Complex` 数 `a+b*im` であれば、`SimpleQuaternion(z)` は `a + b*im + 0*jm + 0*km` を返します。
