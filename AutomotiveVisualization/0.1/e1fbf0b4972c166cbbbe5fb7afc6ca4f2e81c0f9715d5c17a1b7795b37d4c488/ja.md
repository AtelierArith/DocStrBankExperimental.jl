車を表す基本的な描画可能な長方形。矢印は車の進行方向を示します。

```
ArrowCar{A<:AbstractArray{Float64}, C<:Colorant} <: Renderable
ArrowCar(pos::AbstractArray, angle::Float64=0.0; length = 4.8, width = 1.8,  color=colortheme["COLOR_CAR_OTHER"], text="", id=0)
ArrowCar(x::Real, y::Real, angle::Float64=0.0; length = 4.8, width = 1.8,  color=colortheme["COLOR_CAR_OTHER"], text="", id=0)
```
