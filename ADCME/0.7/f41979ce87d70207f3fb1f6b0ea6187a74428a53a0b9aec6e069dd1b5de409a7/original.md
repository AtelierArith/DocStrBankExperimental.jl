```
register(forward::Function, backward::Function; multiple::Bool=false)
```

Register a function `forward` with back-propagated gradients rule `backward` to the backward.  ∘ `forward`: it takes $n$ inputs and outputs $m$ tensors. When $m>1$, the keyword `multiple` must be true.  ∘ `backward`: it takes $\tilde m$ top gradients from float/double output tensors of `forward`, $m$ outputs of the `forward`,     and $n$ inputs of the `forward`. `backward` outputs $n$ gradients for each input of `forward`. When input $i$ of    `forward` is not float/double, `backward` should return `nothing` for the corresponding gradients. 

# Example

```julia
forward = x->log(1+exp(x))
backward = (dy, y, x)->dy*(1-1/(1+y))
f = register(forward, backward)
```
