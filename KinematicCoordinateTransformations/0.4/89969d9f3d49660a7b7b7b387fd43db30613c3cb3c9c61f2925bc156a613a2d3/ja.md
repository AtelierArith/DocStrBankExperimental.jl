```
KinematicTransformation
```

運動量の変換を表す抽象型。

```
(trans::KinematicTransformation)(t, x, [v, [a, [j]]], linear_only::Bool=false)
```

変換 `trans` に従って、時刻 `t` においてソース座標系からターゲット座標系にベクトル `x`、およびオプションで `v`、`a`、`j` を変換し、ターゲット座標系での `x` とオプションで `v`、`a`、`j` を返します。

`v`、`a`、および `j` は `x` の1次から3次の時間微分です。

`linear_only` が `true` の場合、変換の定数部分（もしあれば）は適用されません。たとえば、変換の形 `x_target = A*x_source + b` を表す `ConstantAffineMap` では、`b` は使用されません。これは、点の位置を表さず、その時間微分を持つベクトルを適切に変換するのに便利です（例：力）。
