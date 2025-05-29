```julia
get_parameters(𝓂; values)

```

モデルのダイナミクスに影響を与えるが、他のパラメータに依存せず、キャリブレーション方程式によって決定されないパラメータ（およびオプションで値）を返します。

プログラムによるモデル作成が使用された場合、この関数は解析されたパラメータを返します（`Examples`の`σ`を参照）。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。

# キーワード引数

  * `values` [デフォルト: `false`, 型: `Bool`]: パラメータ名と一緒に値を返します。

# 戻り値

  * `Vector{String}`のパラメータ、または`values`が`true`に設定されている場合はパラメータと値の`Vector{Pair{String, Float64}}`。

# 例

```jldoctest
using MacroModelling

@model RBC begin
    1  /  c[0] = (β  /  c[1]) * (α * exp(z{TFP}[1]) * k[0]^(α - 1) + (1 - exp(z{δ}[1]) * δ))
    c[0] + k[0] = (1 - exp(z{δ}[0])δ) * k[-1] + q[0]
    q[0] = exp(z{TFP}[0]) * k[-1]^α
    for shock in [TFP, δ]
        z{shock}[0] = ρ{shock} * z{shock}[-1] + σ{shock} * (eps{shock}[x] + eps_news{shock}[x-1])
    end
    Δc_share[0] = log(c[0]/q[0]) - log(c[-1]/q[-1])
    Δk_4q[0] = log(k[0]) - log(k[-4])
end

@parameters RBC begin
    σ = 0.01
    ρ = 0.2
    capital_to_output = 1.5
    k[ss] / (4 * q[ss]) = capital_to_output | δ
    alpha = .5
    α = alpha
    β = 0.95
end

get_parameters(RBC)
# output
7-element Vector{String}:
 "σ{TFP}"
 "σ{δ}"
 "ρ{TFP}"
 "ρ{δ}"
 "capital_to_output"
 "alpha"
 "β"
```
