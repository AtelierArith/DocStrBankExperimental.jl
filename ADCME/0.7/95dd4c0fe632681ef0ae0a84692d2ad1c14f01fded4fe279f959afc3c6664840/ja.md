```
BFGS!(sess::PyObject, loss::PyObject, grads::Union{Array{T},Nothing,PyObject}, 
vars::Union{Array{PyObject},PyObject}; kwargs...) where T<:Union{Nothing, PyObject}
```

BFGSアルゴリズムを実行します $\min_{\texttt{vars}} \texttt{loss}(\texttt{vars})$ 勾配 `grads` を提供する必要があります。通常、`grads[i] = gradients(loss, vars[i])` です。 `grads[i]` は異なるデバイス（GPUまたはCPU）に存在する可能性があります。

# 例 1

```julia
import Optim # 必須
a = Variable(0.0)
loss = (a-1)^2
g = gradients(loss, a)
sess = Session(); init(sess)
BFGS!(sess, loss, g, a)
```

# 例 2

```julia
import Optim # 必須
a = Variable(0.0)
loss = (a^2+a-1)^2
g = gradients(loss, a)
sess = Session(); init(sess)
cb = (vs, iter, loss)->begin 
    printstyled("[#iter $iter] a = $vs, loss=$loss\n", color=:green)
end
BFGS!(sess, loss, g, a; callback = cb)
```
