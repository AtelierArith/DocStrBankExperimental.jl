```
Optimize!(sess::PyObject, loss::PyObject, max_iter::Int64 = 15000;
vars::Union{Array{PyObject},PyObject, Missing} = missing, 
grads::Union{Array{T},Nothing,PyObject, Missing} = missing, 
optimizer = missing,
callback::Union{Function, Missing}=missing,
x_tol::Union{Missing, Float64} = missing,
f_tol::Union{Missing, Float64} = missing,
g_tol::Union{Missing, Float64} = missing, kwargs...) where T<:Union{Nothing, PyObject}
```

Optimパッケージやカスタムオプティマイザを使用するためのインターフェースです。

  * `sess`: セッション;
  * `loss`: 損失関数;
  * `max_iter`: 最大反復回数;
  * `vars`, `grads`: 最適化可能な変数と勾配
  * `optimizer`: Optimオプティマイザ（デフォルト: LBFGS）
  * `callback`: 各ラインサーチ完了後のコールバック（ラインサーチの1ステップではない）

他の引数はOptimオプティマイザのOptionsに渡されます。

Ipoptからオプティマイザを構築することもできます。例えば、次のようにオプティマイザを構築します：

```julia
import Ipopt
x = Variable(rand(2))
loss = (1-x[1])^2 + 100(x[2]-x[1]^2)^2

function opt(f, g, fg, x0, kwargs...)
    prob = createProblem(2, -100ones(2), 100ones(2), 0, Float64[], Float64[], 0, 0,
                     f, (x,g)->nothing, (x,G)->g(G, x), (x, mode, rows, cols, values)->nothing, nothing)
    prob.x = x0 
    Ipopt.addOption(prob, "hessian_approximation", "limited-memory")
    status = Ipopt.solveProblem(prob)
    println(Ipopt.ApplicationReturnStatus[status])
    println(prob.x)
    Ipopt.freeProblem(prob)
    nothing
end

sess = Session(); init(sess)
Optimize!(sess, loss, optimizer = opt)
```
