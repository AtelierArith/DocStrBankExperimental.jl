```
DescentResult(;
    δu = missing, u = missing, success::Bool = true, linsolve_success::Bool = true,
    extras = (;)
)
```

`DescentResult`オブジェクトを構築します。

### キーワード引数

  * `δu`: 降下方向。
  * `u`: 新しい反復値。これは現在、マルチステップ法のみに提供されます。
  * `success`: 特定の降下アルゴリズムは、例えば[`GeodesicAcceleration`](@ref)のように降下方向を拒否することがあります。
  * `linsolve_success`: ラインサーチが成功したかどうか。
  * `extras`: 解決中に計算された中間結果を含む名前付きタプル。例えば、[`GeodesicAcceleration`](@ref)は「速度」と「加速度」項を含む`NamedTuple{(:v, :a)}`を返します。
