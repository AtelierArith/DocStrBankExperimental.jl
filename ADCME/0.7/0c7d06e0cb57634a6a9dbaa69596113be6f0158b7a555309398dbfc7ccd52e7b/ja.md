```
newton_raphson_with_grad(f::Function, 
u0::Union{Array,PyObject}, 
θ::Union{Missing,PyObject, Array{<:Real}}=missing,
args::PyObject...) where T<:Real
```

微分可能なニュートン-ラフソンアルゴリズム。 [`newton_raphson`](@ref)を参照してください。

`ADCME.options.newton_raphson`を使用してオプションを指定します。

# 例

```julia
function f(θ, x)
    x^3 - θ, 3spdiag(x^2)
end

θ = constant([2. .^3;3. ^3; 4. ^3])
x = newton_raphson_with_grad(f, constant(ones(3)), θ)
run(sess, x)≈[2.;3.;4.]
run(sess, gradients(sum(x), θ))
```
