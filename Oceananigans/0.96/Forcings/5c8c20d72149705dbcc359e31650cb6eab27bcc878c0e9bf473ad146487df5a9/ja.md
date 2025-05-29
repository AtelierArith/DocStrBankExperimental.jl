```
Forcing(func; parameters=nothing, field_dependencies=(), discrete_form=false)
```

モデルフィールドの傾向に追加できる `Forcing` `func`ションを返します。

`discrete_form=false`（デフォルト）の場合、`parameters` または `field_dependencies` が提供されていない場合、`func` は次のシグネチャで呼び出せる必要があります。

```
func(x, y, z, t)
```

ここで `x, y, z` は東西、南北、垂直の空間座標で、`t` は時間です。この形式は `NonhydrostaticModel` のコンストラクタでもデフォルトであるため、`Forcing` は必要ありません。

`discrete_form=false`（デフォルト）の場合、`field_dependencies` が提供されていると、`func` のシグネチャにはそれらが含まれている必要があります。たとえば、`field_dependencies=(:u, :S)`（`parameters` は提供されていない場合）、`func` は次のシグネチャで呼び出せる必要があります。

```
func(x, y, z, t, u, S)
```

ここで `u` は `u`-速度成分であり、`S` はトレーサーと見なされます。`u`、`v`、または `w` という名前を持たないフィールドはトレーサーと見なされ、`model.tracers` に存在する必要があります。

`discrete_form=false`（デフォルト）の場合、`parameters` が提供されていると、`func` の*最後の*引数は `parameters` でなければなりません。たとえば、`func` に `field_dependencies` がないが `parameters` に依存している場合、次のシグネチャで呼び出せる必要があります。

```
func(x, y, z, t, parameters)
```

オブジェクト `parameters` は原則として任意ですが、GPU コンパイルは `typeof(parameters)` に制約を課すことがあります。

`field_dependencies=(:u, :v, :w, :c)` と `parameters` がある場合、`func` は次のシグネチャで呼び出せる必要があります。

```
func(x, y, z, t, u, v, w, c, parameters)
```

`discrete_form=true` の場合、`func` は「離散形式」で呼び出せる必要があります。

```
func(i, j, k, grid, clock, model_fields)
```

ここで `i, j, k` は強制が適用されるグリッドポイントで、`grid` は `model.grid`、`clock.time` は現在のシミュレーション時間、`clock.iteration` は現在のモデルイテレーション、`model_fields` は `u, v, w`、`model.tracers` のフィールド、`model.diffusivity_fields` のフィールドを持つ `NamedTuple` であり、それぞれがフィールドデータの `OffsetArray`（または乱流閉じ込めに応じた `OffsetArray` の `NamedTuple`）です。

`discrete_form=true` で `parameters` が*指定されている*場合、`func` は次のシグネチャで呼び出せる必要があります。

```
func(i, j, k, grid, clock, model_fields, parameters)
```

# 例

```jldoctest forcing
using Oceananigans

# パラメータ化された強制
parameterized_func(x, y, z, t, p) = p.μ * exp(z / p.λ) * cos(p.ω * t)

v_forcing = Forcing(parameterized_func, parameters = (μ=42, λ=0.1, ω=π))

# 出力
ContinuousForcing{@NamedTuple{μ::Int64, λ::Float64, ω::Irrational{:π}}}
├── func: parameterized_func (generic function with 1 method)
├── parameters: (μ = 42, λ = 0.1, ω = π)
└── field dependencies: ()
```

強制位置が `NonhydrostaticModel` コンストラクタ内で正規化されるため、次のようになります。

```jldoctest forcing
grid = RectilinearGrid(size=(1, 1, 1), extent=(1, 1, 1))
model = NonhydrostaticModel(grid=grid, forcing=(v=v_forcing,))

model.forcing.v

# 出力
ContinuousForcing{@NamedTuple{μ::Int64, λ::Float64, ω::Irrational{:π}}} at (Center, Face, Center)
├── func: parameterized_func (generic function with 1 method)
├── parameters: (μ = 42, λ = 0.1, ω = π)
└── field dependencies: ()
```

`NonhydrostaticModel` のコンストラクタを通過した後、`v`-強制位置情報が利用可能になり、`Center, Face, Center` に設定されます。

```jldoctest forcing
# フィールド依存の強制
growth_in_sunlight(x, y, z, t, P) = exp(z) * P

plankton_forcing = Forcing(growth_in_sunlight, field_dependencies=:P)

# 出力
ContinuousForcing{Nothing}
├── func: growth_in_sunlight (generic function with 1 method)
├── parameters: nothing
└── field dependencies: (:P,)
```

```jldoctest forcing
# パラメータ化され、フィールド依存の強制
tracer_relaxation(x, y, z, t, c, p) = p.μ * exp((z + p.H) / p.λ) * (p.dCdz * z - c)

c_forcing = Forcing(tracer_relaxation,
                    field_dependencies = :c,
                            parameters = (μ=1/60, λ=10, H=1000, dCdz=1))

# 出力
ContinuousForcing{@NamedTuple{μ::Float64, λ::Int64, H::Int64, dCdz::Int64}}
├── func: tracer_relaxation (generic function with 1 method)
├── parameters: (μ = 0.016666666666666666, λ = 10, H = 1000, dCdz = 1)
└── field dependencies: (:c,)
```

```jldoctest forcing
# パラメータなしの離散形式の強制関数
filtered_relaxation(i, j, k, grid, clock, model_fields) =
    @inbounds - (model_fields.c[i-1, j, k] + model_fields.c[i, j, k] + model_fields.c[i+1, j, k]) / 3

filtered_forcing = Forcing(filtered_relaxation, discrete_form=true)

# 出力
DiscreteForcing{Nothing}
├── func: filtered_relaxation (generic function with 1 method)
└── parameters: nothing
```

```jldoctest forcing
# パラメータ付きの離散形式の強制関数
masked_damping(i, j, k, grid, clock, model_fields, parameters) =
    @inbounds - parameters.μ * exp(grid.z.cᵃᵃᶜ[k] / parameters.λ) * model_fields.u[i, j, k]

masked_damping_forcing = Forcing(masked_damping, parameters=(μ=42, λ=π), discrete_form=true)

# 出力
DiscreteForcing{@NamedTuple{μ::Int64, λ::Irrational{:π}}}
├── func: masked_damping (generic function with 1 method)
└── parameters: (μ = 42, λ = π)
```
