```julia
DigitalShift <: ScrambleMethod
```

Digital shift. `randomize(x, R::DigitalShift)` returns a scrambled version of `x`.

The scramble method is Digital Shift. It scrambles each coordinate in base `b` as `yₖ = (xₖ + Uₖ) mod b` where `Uₖ ∼ 𝕌({0:b-1})`. `U` is the same for every point `points` but i.i.d. along every dimension.
