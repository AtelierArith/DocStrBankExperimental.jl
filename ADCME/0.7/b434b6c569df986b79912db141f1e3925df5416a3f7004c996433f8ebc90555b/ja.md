```
NonlinearConstrainedProblem(f::Function, L::Function, θ::PyObject, u0::Union{PyObject, Array{Float64}}; options::Union{Dict{String, T}, Missing}=missing) where T<:Integer
```

勾配 $\frac{\partial L}{\partial \theta}$ を計算します。

$$
\min \ L(u) \quad \mathrm{s.t.} \ F(\theta, u) = 0
$$

`u0` は数値解 `u` の初期推定値です。 [`newton_raphson`](@ref) を参照してください。

注意点: `r, A = f(θ, u)` と `θ` は未知のパラメータであり、`gradients(r, θ)` は定義されている必要があります（バックプロパゲーションが正しく機能します）。

返り値: タプル (`L`: 損失, `C`: 制約, `Graidents`) を返します。

$$
\left(L(u), u, \frac{\partial L}{\partial θ}\right)
$$

# 例

次の制約付き最適化問題を解きたいと思います。 $\begin{aligned}\min_\theta &\; L(u) = (u-1)^3\\ \text{s.t.} &\; u^3 + u = \theta\end{aligned}$ 解は $\theta = 2$ です。Julia コードは次の通りです。

```julia
function f(θ, u)
    u^3 + u - θ, spdiag(3u^2+1) 
end
function L(u) 
    sum((u-1)^2)
end
pl = Variable(ones(1))
l, θ, dldθ = NonlinearConstrainedProblem(f, L, pl, ones(1))
```

これを数学的最適化器と組み合わせることができます。

```julia
using Optim 
sess = Session(); init(sess)
BFGS!(sess, l, dldθ, pl) 
```
