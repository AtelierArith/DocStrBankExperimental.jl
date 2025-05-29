```
mutable struct SinusoidalTemperature <: Temperature
    a::Float64
    b::Int64
    c::Int64
    d::Float64
end
```

シミュレーションのためのデータで、°Cでの正弦波温度変動を特徴としています。南半球に適用可能な`cosine`実装を使用しています。内部で生成されます。

# 引数

  * `a::Float64`: 振幅。
  * `b::Float64`: 周期係数。
  * `c::Float64`: 時間期間（日）。
  * `d::Float64`: 平均。
