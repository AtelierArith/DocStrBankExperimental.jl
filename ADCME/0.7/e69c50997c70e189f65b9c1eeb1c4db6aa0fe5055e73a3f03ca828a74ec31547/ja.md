```
jacview(sess::PyObject, f::Function, θ::Union{Array{Float64}, PyObject, Missing}, 
u0::Array{Float64}, args...)
```

ベクトル関数の勾配テストを実行します。`f` のシグネチャは 

```
f(θ, u) -> r, J
```

ここで `θ` は煩わしいパラメータ、`u` は状態変数（ヤコビ行列が計算される対象）、`r` は残差ベクトル、`J` はヤコビ行列（密行列または [`SparseTensor`](@ref)）です。

# 例 1

```julia
u0 = rand(10)
function verify_jacobian_f(θ, u)
    r = u^3+u - u0
    r, spdiag(3u^2+1.0)
end
jacview(sess, verify_jacobian_f, missing, u0)
```

# 例 2

```
u0 = rand(10)
rs = rand(10)
function verify_jacobian_f(θ, u)
    r = [u^2;u] - [rs;rs]
    r, [spdiag(2*u); spdiag(10)]
end
jacview(sess, verify_jacobian_f, missing, u0); close("all")
```
