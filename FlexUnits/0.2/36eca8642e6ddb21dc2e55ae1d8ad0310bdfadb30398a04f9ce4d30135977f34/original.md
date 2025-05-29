```
UnitfulCallable{T<:Any, UI<:Any, UO<:Any}
```

An object representing a callable object that requires inputs to be units UI and produces outputs of UO This is useful for wrapping functions/models that aren't generic enough to support `Quantity` types.

Example1: Applying quantities to a strictly Real function

```
angle_coords(θ::Real, r::Real) = r.*(cos(θ), sin(θ))
unitful_angle_coords = UnitfulCallable(angle_coords, (u"", u"m") => dimension(u"m"))

c = unitful_angle_coords(30u"deg", 6u"cm")
```

Example2: Applying quantities to a strictly Real model

```
struct RotatingArm
    len :: Float64
end

angle_coords(arm::RotatingArm, θ::Real) = arm.len.*(cos(θ), sin(θ))
angle_coords(arm::Quantity{<:RotatingArm}, θ::Quantity{<:Real}) = UnitfulCallable(Base.Fix1(angle_coords, ustrip(arm)), u""=>unit(arm))(θ)

c = angle_coords(Quantity(RotatingArm(1.0), u"m"), 30u"deg")
```
