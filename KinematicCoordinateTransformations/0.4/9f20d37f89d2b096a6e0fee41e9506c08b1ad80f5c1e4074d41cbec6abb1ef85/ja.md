```
transform(trans::KinematicTransformation, t, x, [v, [a, [j]]], linear_only::Bool=false)
```

ベクトル `x` を、オプションで `v`、`a`、および `j` を、変換 `trans` に従って、時刻 `t` においてソース座標系からターゲット座標系に変換し、ターゲット座標系での `x` とオプションで `v`、`a`、および `j` を返します。

`v`、`a`、および `j` は、`x` の1回目から3回目の時間微分です。

`linear_only` が `true` の場合、変換の定数部分（もしあれば）は適用されません。たとえば、`x_target = A*x_source + b` の形の変換を表す `ConstantAffineMap` では、`b` は使用されません。これは、点の位置を表さないベクトルやその時間微分（例：力）を適切に変換するのに役立ちます。
