```julia
get_equations(𝓂)

```

モデルの方程式を返します。プログラムによるモデル記述が使用された場合、この関数は解析された方程式を返します（`Examples`のショックのループを参照）。

# 引数

  * `𝓂`: [`@model`](@ref) および [`@parameters`](@ref) によって作成されたオブジェクト。

# 戻り値

  * 解析された方程式の `Vector{String}`。

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

get_equations(RBC)
# 出力
7-element Vector{String}:
 "1 / c[0] = (β / c[1]) * (α * ex" ⋯ 25 bytes ⋯ " - 1) + (1 - exp(z{δ}[1]) * δ))"
 "c[0] + k[0] = (1 - exp(z{δ}[0]) * δ) * k[-1] + q[0]"
 "q[0] = exp(z{TFP}[0]) * k[-1] ^ α"
 "z{TFP}[0] = ρ{TFP} * z{TFP}[-1]" ⋯ 18 bytes ⋯ "TFP}[x] + eps_news{TFP}[x - 1])"
 "z{δ}[0] = ρ{δ} * z{δ}[-1] + σ{δ} * (eps{δ}[x] + eps_news{δ}[x - 1])"
 "Δc_share[0] = log(c[0] / q[0]) - log(c[-1] / q[-1])"
 "Δk_4q[0] = log(k[0]) - log(k[-4])"
```
