```
neural2([rng,] network; transform=log, inverse=exp)
```

Lux.jl ニューラルネットワーク `network` を初期化し、体積成長に関連する二次元ニューラル ODE を解くための呼び出し可能なオブジェクト `model` を返します。詳細は以下の「基礎 ODE」を参照してください。

返されたオブジェクト `model` は次のように呼び出されます：

```
volumes = model(times, p)
```

ここで、`p` は `v0`、`v∞`、`θ` のプロパティを持つ必要があります。`v0` は初期体積（したがって `volumes[1] = v0`）、`v∞` は体積スケールパラメータ、`θ` は `network` に対応する Lux.jl パラメータです。

キャリブレーションは `v∞` が固定されているときに最も効果的であるようです。

`θ` の形式は `TumorGrowth.initial_parameters(model)` と同じであり、これは関連する [`CalibrationProblem`](@ref) を解く際に使用されるデフォルトの初期値でもあります。

```julia
using Lux, Random

# 2つの入力と2つの出力を持つニューラルネットワークを定義：
network = Lux.Chain(Dense(2, 3, Lux.tanh; init_weight=Lux.zeros64), Dense(3, 2))

rng = Xoshiro(123)
model = neural2(rng, network)
θ = TumorGrowth.initial_parameters(model)
times = [0.1, 6.0, 16.0, 24.0, 32.0, 39.0]
v0, v∞ = 0.00023, 0.00015
p = (; v0, v∞, θ)

julia> volumes = model(times, p) # (ゼロ初期化のため定数)
6-element Vector{Float64}:
 0.00023
 0.00023
 0.00023
 0.00023
 0.00023
 0.00023
```

# 基礎 ODE

固定パラメータ `θ` を持つニューラルネットワークを数学的関数 $f$ として見なし、コンポーネント $f₁$ と $f₂$ を持ち、`transform` 関数を $ϕ$ と書きます。すると $v(t) = v_∞ ϕ^{-1}(y(t))$ となり、$y(t)$ と潜在変数 $u(t)$ は次のように進化します。

$$
dy/dt = f₁(y, u)
$$

$$
du/dt = f₂(y, u)
$$

初期条件 $y(t₀) = ϕ(v₀/v_∞)$、$u(t₀) = 1$ に従います。ここで $t₀$ は初期時間であり、`times[1]` です。私たちは $v₀$=`v0` および $v_∞$=`v∞` と書いています。

すべてのモデルのリストについては [`TumorGrowth`](@ref) を参照してください。さらに [`CalibrationProblem`](@ref) も参照してください。
