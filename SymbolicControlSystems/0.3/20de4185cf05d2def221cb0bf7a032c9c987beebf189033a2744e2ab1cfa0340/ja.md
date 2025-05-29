```
doubleeuler(sys::AbstractStateSpace{<:Continuous}, Ts)
```

`sys`を指数写像の2次近似で離散化します（フォワードオイラーは1次近似です）。これは、真のZoH離散化のための記号式があまりにも複雑になる場合に便利です。2次近似は、場合によっては真のZoH離散化に近いですが、バランスの取れた状態空間実現が必要です。[`pade_zoh`](@ref)も参照してください。

# 例

```julia
w = 2pi .* exp10.(LinRange(-1, log10(25), 400))
sys = ssrand(1,1,4)
bodeplot(sys, w, lab="cont")
bodeplot!(c2d(sys, 0.001, :fwdeuler), w, label="fwdeuler")
bodeplot!(doubleeuler(sys, 0.001), w, label="double euler")
```
