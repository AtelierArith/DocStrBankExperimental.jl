```
UnitfulCallable{T<:Any, UI<:Any, UO<:Any}
```

UIの単位を必要とし、UOの出力を生成する呼び出し可能なオブジェクトを表します。これは、`Quantity`型をサポートするには一般的すぎない関数/モデルをラップするのに便利です。

例1: 厳密な実数関数に量を適用する

```
angle_coords(θ::Real, r::Real) = r.*(cos(θ), sin(θ))
unitful_angle_coords = UnitfulCallable(angle_coords, (u"", u"m") => dimension(u"m"))

c = unitful_angle_coords(30u"deg", 6u"cm")
```

例2: 厳密な実数モデルに量を適用する

```
struct RotatingArm
    len :: Float64
end

angle_coords(arm::RotatingArm, θ::Real) = arm.len.*(cos(θ), sin(θ))
angle_coords(arm::Quantity{<:RotatingArm}, θ::Quantity{<:Real}) = UnitfulCallable(Base.Fix1(angle_coords, ustrip(arm)), u""=>unit(arm))(θ)

c = angle_coords(Quantity(RotatingArm(1.0), u"m"), 30u"deg")
```
