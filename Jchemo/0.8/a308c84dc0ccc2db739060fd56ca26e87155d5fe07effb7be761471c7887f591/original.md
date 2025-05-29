```
softmax(x::AbstractVector)
softmax(X::Union{Matrix, DataFrame})
```

Softmax function.

  * `x` : A vector to transform.
  * `X` : A matrix whose rows are transformed.

Let v be a vector:

  * 'softmax'(v) = exp.(v) / sum(exp.(v))

## Examples

```julia
using Jchemo

x = 1:3
softmax(x)

X = rand(5, 3)
softmax(X)
```
