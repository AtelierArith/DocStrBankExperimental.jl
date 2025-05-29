```julia
get_dynamic_equations(𝓂)

```

モデルのダイナミクスを説明する拡張された方程式系を返します。拡張されたとは、リードまたはラグが1より大きい変数や、リードまたはラグを持つ外生的ショックの場合に、リードまたはラグの変数を含む補助方程式によってシステムが拡張されることを意味します。拡張されたシステムは、現在 `[0]`、未来 `[1]`、または過去 `[-1]` にある変数のみを特徴とします。例えば、`Δk_4q[0] = log(k[0]) - log(k[-3])` は `k[-3]` を含みます。2つの補助変数（`kᴸ⁽⁻¹⁾` と `kᴸ⁽⁻²⁾`、ここで `ᴸ` はリード/ラグ演算子）を導入し、システムを拡張することで（`kᴸ⁽⁻²⁾[0] = kᴸ⁽⁻¹⁾[-1]` および `kᴸ⁽⁻¹⁾[0] = k[-1]`）、絶対値でのタイミングが1未満であることを保証できます：`Δk_4q[0] - (log(k[0]) - log(kᴸ⁽⁻²⁾[-1]))`。

プログラムによるモデル記述が使用された場合、この関数は解析された方程式を返します（例のショックのループを参照）。

出力は方程式が0に等しいことを前提としています。つまり、`kᴸ⁽⁻¹⁾[0] - k[-1]` は `kᴸ⁽⁻¹⁾[0] - k[-1] = 0` を意味し、したがって：`kᴸ⁽⁻¹⁾[0] = k[-1]` となります。

# 引数

  * `𝓂`: [`@model`](@ref) および [`@parameters`](@ref) によって作成されたオブジェクト。

# 戻り値

  * 動的モデル方程式の `Vector{String}`。

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

get_dynamic_equations(RBC)
# output
12-element Vector{String}:
 "1 / c[0] - (β / c[1]) * (α * ex" ⋯ 25 bytes ⋯ " - 1) + (1 - exp(z{δ}[1]) * δ))"
 "(c[0] + k[0]) - ((1 - exp(z{δ}[0]) * δ) * k[-1] + q[0])"
 "q[0] - exp(z{TFP}[0]) * k[-1] ^ α"
 "eps_news{TFP}[0] - eps_news{TFP}[x]"
 "z{TFP}[0] - (ρ{TFP} * z{TFP}[-1] + σ{TFP} * (eps{TFP}[x] + eps_news{TFP}[-1]))"
 "eps_news{δ}[0] - eps_news{δ}[x]"
 "z{δ}[0] - (ρ{δ} * z{δ}[-1] + σ{δ} * (eps{δ}[x] + eps_news{δ}[-1]))"
 "Δc_share[0] - (log(c[0] / q[0]) - log(c[-1] / q[-1]))"
 "kᴸ⁽⁻³⁾[0] - kᴸ⁽⁻²⁾[-1]"
 "kᴸ⁽⁻²⁾[0] - kᴸ⁽⁻¹⁾[-1]"
 "kᴸ⁽⁻¹⁾[0] - k[-1]"
 "Δk_4q[0] - (log(k[0]) - log(kᴸ⁽⁻³⁾[-1]))"
```
