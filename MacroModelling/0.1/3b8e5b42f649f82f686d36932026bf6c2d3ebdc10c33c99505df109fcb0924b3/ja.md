```julia
get_calibration_equations(𝓂)

```

`@parameters`ブロックで宣言されたキャリブレーション方程式を返します。キャリブレーション方程式は、非確率的定常状態問題の一部である追加の方程式です。追加の方程式は、`@model`ブロックで宣言された方程式の一部であるキャリブレートされたパラメータと一致し、次のように取得できます: `get_calibrated_parameters`

プログラムによるモデル記述が使用された場合、この関数は解析された方程式を返します（例のショックのループを参照）。

出力は方程式が0に等しいと仮定しています。つまり、`k / (q * 4) - capital_to_output`は`k / (q * 4) - capital_to_output = 0`を意味し、したがって: `k / (q * 4) = capital_to_output`となります。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。

# 戻り値

  * キャリブレーション方程式の`Vector{String}`。

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

get_calibration_equations(RBC)
# output
1-element Vector{String}:
 "k / (q * 4) - capital_to_output"
```
