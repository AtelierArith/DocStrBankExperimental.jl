```julia
get_parameters_in_equations(𝓂)

```

モデル方程式に含まれるパラメータを返します。これらのパラメータは、`@parameters`ブロックで定義された他のパラメータやキャリブレーション方程式によって決定される可能性があることに注意してください。

プログラムによるモデル記述が使用された場合、この関数は解析されたパラメータを返します（`Examples`の`σ`を参照）。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。

# 戻り値

  * パラメータの`Vector{String}`。

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

get_parameters_in_equations(RBC)
# output
7-element Vector{String}:
 "α"
 "β"
 "δ"
 "ρ{TFP}"
 "ρ{δ}"
 "σ{TFP}"
 "σ{δ}"
```
