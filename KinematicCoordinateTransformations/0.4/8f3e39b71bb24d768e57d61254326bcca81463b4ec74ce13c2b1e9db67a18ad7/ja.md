```
transform!(x_new, [v_new, [a_new, [j_new]]], trans::KinematicTransformation, t, x, [v, [a, [j]]], linear_only::Bool=false)
```

ベクトル `x` を変換し、オプションで `v`、`a`、および `j` をソース座標系からターゲット座標系に時間 `t` に従って変換 `trans` に基づいて、結果を `x_new` に、オプションで `v_new`、`a_new`、および `j_new` をターゲット座標系に返します。

`v`、`a`、および `j` は `x` の1回目から3回目の時間微分です。

`linear_only` が `true` の場合、変換の定数部分（もしあれば）は適用されません。たとえば、`x_target = A*x_source + b` の形の変換を表す `ConstantAffineMap` では、`b` は使用されません。これは、点の位置を表さず、その時間微分を持つベクトルを適切に変換するのに便利です（例：力）。
