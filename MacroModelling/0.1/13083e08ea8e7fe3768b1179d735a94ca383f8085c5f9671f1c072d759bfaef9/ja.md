```julia
get_dynamic_auxilliary_variables(𝓂)

```

モデルのダイナミクスを説明する拡張された方程式系の一部である、タイミングの下付き文字のない補助変数を返します。拡張されたとは、リードまたはラグが1より大きい変数や、リードまたはラグを持つ外生的ショックがある場合に、リードまたはラグに含まれる変数やショックを含む補助変数によってシステムが拡張されることを意味します。元の方程式にはリードまたはラグを持つ変数が含まれているため、特定の表現は負になることができません（例：`log(c/q)`が与えられた場合、`c/q`のための補助変数が作成されます）。

補助変数と方程式の詳細については、`get_dynamic_equations`を参照してください。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。

# 戻り値

  * 補助パラメータの`Vector{String}`。

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

get_dynamic_auxilliary_variables(RBC)
# output
3-element Vector{String}:
 "kᴸ⁽⁻²⁾"
 "kᴸ⁽⁻³⁾"
 "kᴸ⁽⁻¹⁾"
```
