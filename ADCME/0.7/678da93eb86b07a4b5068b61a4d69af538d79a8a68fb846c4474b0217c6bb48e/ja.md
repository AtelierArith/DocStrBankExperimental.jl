```
BFGS!(sess::PyObject, loss::PyObject, max_iter::Int64=15000; 
vars::Array{PyObject}=PyObject[], callback::Union{Function, Nothing}=nothing, method::String = "L-BFGS-B", kwargs...)
```

`BFGS!` は **L-BFGS-B** オプティマイザの簡略化されたインターフェースです。詳細は [`ScipyOptimizerInterface`](@ref) を参照してください。`callback` は次のシグネチャを持つコールバック関数です。

```julia
callback(vs::Array, iter::Int64, loss::Float64)
```

`vars` はテンソルで構成された配列で、その値が `vs` への入力となります。

# 例 1

```julia
a = Variable(1.0)
loss = (a - 10.0)^2
sess = Session(); init(sess)
BFGS!(sess, loss)
```

# 例 2

```julia
θ1 = Variable(1.0)
θ2 = Variable(1.0)
loss = (θ1-1)^2 + (θ2-2)^2
cb = (vs, iter, loss)->begin 
    printstyled("[#iter $iter] θ1=$(vs[1]), θ2=$(vs[2]), loss=$loss\n", color=:green)
end
sess = Session(); init(sess)
cb(run(sess, [θ1, θ2]), 0, run(sess, loss))
BFGS!(sess, loss, 100; vars=[θ1, θ2], callback=cb)
```

# 例 3

`bounds` を使用して変数の上限と下限を指定します。

```julia
x = Variable(2.0)    
loss = x^2
sess = Session(); init(sess)
BFGS!(sess, loss, bounds=Dict(x=>[1.0,3.0]))
```

!!! note
    ユーザーは `method` キーワード引数を提供することで、他の scipy 最適化アルゴリズムを使用することもできます。たとえば、BFGS オプティマイザを使用することができます。

    ```julia
    BFGS!(sess, loss, method = "BFGS")
    ```

