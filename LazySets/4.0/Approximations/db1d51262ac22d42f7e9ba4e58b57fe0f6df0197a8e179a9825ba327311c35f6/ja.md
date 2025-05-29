```
underapproximate(X::S, dirs::AbstractDirections;
                [apply_convex_hull]::Bool=false) where {N, S<:LazySet{N}}
```

凸集合のサポートベクトルをサンプリングすることによって、アンダー近似を計算します。

### 入力

  * `X`                 – 凸集合
  * `dirs`              – 方向
  * `apply_convex_hull` – （オプション、デフォルト: `false`）`true`の場合、サポートベクトルを凸包操作で後処理します

### 出力

`dirs`によって決定された方向に沿った`X`のサポートベクトルの凸包を取ることによって得られる`VPolytope`。

### 注意事項

サポートベクトルは常に一意でないため、このアルゴリズムは、与えられたテンプレートを使用して正確に近似できる場合でも、厳密なアンダー近似を返すことがあります。
