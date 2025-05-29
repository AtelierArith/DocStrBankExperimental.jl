```
batch_ss(sys, inputs, outputs, ops::AbstractVector{<:AbstractDict};
            t = 0.0,
            allow_input_derivatives = false,
            kwargs...)
```

複数の動作点 `ops::Vector{Dict}` で `sys` を線形化します。`StateSpace` オブジェクトのベクトルと簡略化されたシステムを返します。

# 例:

```
using ControlSystemsMTK, ModelingToolkit, RobustAndOptimalControl
using ModelingToolkit: getdefault
unsafe_comparisons(true)

# モデルを作成
@parameters t k=10 k3=2 c=1
@variables x(t)=0 [bounds = (-2, 2)]
@variables v(t)=0
@variables u(t)=0
@variables y(t)=0

D = Differential(t)

eqs = [D(x) ~ v
       D(v) ~ -k * x - k3 * x^3 - c * v + 10u
       y ~ x]


@named duffing = ODESystem(eqs, t)

bounds = getbounds(duffing, unknowns(duffing))
sample_within_bounds((l, u)) = (u - l) * rand() + l
# 動作点のベクトルを作成
ops = map(1:N) do i
    op = Dict(x => sample_within_bounds(bounds[x]) for x in keys(bounds) if isfinite(bounds[x][1]))
end

Ps, ssys = batch_ss(duffing, [u], [y], ops)
w = exp10.(LinRange(-2, 2, 200))
bodeplot(Ps, w)
P = RobustAndOptimalControl.ss2particles(Ps) # `Particles` を係数として持つ単一の StateSpace システムに変換します。
bodeplot(P, w) # 上記と似たように見えるはずです
```

上記の線形化されたモデルの調整も行いましょう

```
function batch_tune(f, Ps)
    f.(Ps)
end

Cs = batch_tune(Ps) do P
    # C, kp, ki, fig, CF = loopshapingPI(P, 6; phasemargin=45)
    C, kp, ki, kd, fig, CF = loopshapingPID(P, 6; Mt=1.3, Tf = 1/100)
    ss(CF)
end

P = RobustAndOptimalControl.ss2particles(Ps)
C = RobustAndOptimalControl.ss2particles(Cs)

nyquistplot(P * C,
            w,
            ylims = (-10, 3),
            xlims = (-5, 10),
            points = true,
            Ms_circles = [1.5, 2],
            Mt_circles = [1.5, 2])

# 各周波数のニクイスト曲線を囲む円をフィットさせる
centers, radii = fit_complex_perturbations(P * C, w; relative = false, nominal = :center)
nyquistcircles!(w, centers, radii, ylims = (-4, 1), xlims = (-3, 4))
```

[`trajectory_ss`](@ref) と [`fuzz`](@ref) も参照してください。
