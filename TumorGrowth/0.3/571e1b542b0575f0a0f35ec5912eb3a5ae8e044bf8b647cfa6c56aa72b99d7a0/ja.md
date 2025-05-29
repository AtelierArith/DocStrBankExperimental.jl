```
neural([rng,] network; transform=log, inverse=exp)
```

Lux.jl ニューラルネットワーク `network` を初期化し、体積成長に関連する一次元ニューラル ODE を解くための呼び出し可能なオブジェクト `model` を返します。詳細は以下の「基礎となる ODE」を参照してください。

返されたオブジェクト `model` は次のように呼び出されます：

```
volumes = model(times, p)
```

ここで、`p` は `v0`、`v∞`、`θ` のプロパティを持つ必要があります。`v0` は初期体積（したがって `volumes[1] = v0`）、`v∞` は体積スケールパラメータ、`θ` は `network` と互換性のある Lux.jl パラメータです。

キャリブレーションは `v∞` が固定されているときに最も効果的に機能するようです。

`θ` の形式は `TumorGrowth.initial_parameters(model)` と同じであり、これは関連する [`CalibrationProblem`](@ref) を解く際に使用されるデフォルトの初期値でもあります。

```julia
using Lux, Random

# 入力1、出力1のニューラルネットワークを定義：
network = Lux.Chain(Dense(1, 3, Lux.tanh; init_weight=Lux.zeros64), Dense(3, 1))

rng = Xoshiro(123)
model = neural(rng, network)
θ = TumorGrowth.initial_parameters(model)
times = [0.1, 6.0, 16.0, 24.0, 32.0, 39.0]
v0, v∞ = 0.00023, 0.00015
p = (; v0, v∞, θ)

julia> volumes = model(times, p) # (ゼロ初期化のため定数)
6-element Vector{Float64}:
 0.00023
 0.00023
 0.00023
 0.00023# # Neural2
```

# 基礎となる ODE

固定パラメータ `θ` を持つニューラルネットワークを数学的関数 $f$ と見なし、`transform` 関数を $ϕ$ と書きます。すると $v(t) = v_∞ ϕ^{-1}(y(t))$ となり、$y(t)$ は次のように進化します。

$$
dy/dt = f(y)
$$

初期条件 $y(t₀) = ϕ(v_0/v_∞)$ に従い、ここで $t₀$ は初期時間 `times[1]` です。$v₀$=`v0` および $v_∞$=`v∞` と書いています。

すべてのモデルのリストについては [`TumorGrowth`](@ref) を参照してください。さらに [`CalibrationProblem`](@ref) も参照してください。
