```
BFGS!(sess::PyObject, loss::PyObject, grads::Union{Array{T},Nothing,PyObject}, 
vars::Union{Array{PyObject},PyObject}; kwargs...) where T<:Union{Nothing, PyObject}
```

Running BFGS algorithm $\min_{\texttt{vars}} \texttt{loss}(\texttt{vars})$ The gradients `grads` must be provided. Typically, `grads[i] = gradients(loss, vars[i])`.  `grads[i]` can exist on different devices (GPU or CPU). 

# Example 1

```julia
import Optim # required
a = Variable(0.0)
loss = (a-1)^2
g = gradients(loss, a)
sess = Session(); init(sess)
BFGS!(sess, loss, g, a)
```

# Example 2

```julia
import Optim # required
a = Variable(0.0)
loss = (a^2+a-1)^2
g = gradients(loss, a)
sess = Session(); init(sess)
cb = (vs, iter, loss)->begin 
    printstyled("[#iter $iter] a = $vs, loss=$loss\n", color=:green)
end
BFGS!(sess, loss, g, a; callback = cb)
```
