```julia
get_steady_state_equations(𝓂)

```

モデルの非確率的定常状態（NSSS）方程式を返します。`@model`ブロックで書かれた方程式との違いは、外生的ショックが`0`に設定され、時間の添字が排除され（例：`c[-1]`は`c`になります）、自明な簡略化が行われ（例：`log(k) - log(k) = 0`）、負にならない表現のために補助変数が追加されることです。

補助変数はNSSS問題の解決を容易にします。このパッケージは、負にならない表現を補助変数で置き換え、NSSSを決定する方程式系に別の方程式を追加します。例えば、`log(c/q)`は負にならず、`c/q`は補助変数`➕₁`で置き換えられ、追加の方程式が追加されます：`➕₁ = c / q`。

出力は方程式が0に等しいと仮定しています。つまり、`-z{δ} * ρ{δ} + z{δ}`は`-z{δ} * ρ{δ} + z{δ} = 0`を意味し、したがって：`z{δ} * ρ{δ} = z{δ}`です。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。

# 戻り値

  * NSSS方程式の`Vector{String}`。

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

get_steady_state_equations(RBC)
# output
9-element Vector{String}:
 "(-β * ((k ^ (α - 1) * α * exp(z{TFP}) - δ * exp(z{δ})) + 1)) / c + 1 / c"
 "((c - k * (-δ * exp(z{δ}) + 1)) + k) - q"
 "-(k ^ α) * exp(z{TFP}) + q"
 "-z{TFP} * ρ{TFP} + z{TFP}"
 "-z{δ} * ρ{δ} + z{δ}"
 "➕₁ - c / q"
 "➕₂ - c / q"
 "(Δc_share - log(➕₁)) + log(➕₂)"
 "Δk_4q - 0"
```
