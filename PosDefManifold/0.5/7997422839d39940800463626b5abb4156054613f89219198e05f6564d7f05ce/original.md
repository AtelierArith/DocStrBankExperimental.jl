```
softmax(χ::Vector{T}) where T<:Real
```

Given a real vector of $k$ non-negative scores $χ=c_1,...,c_k$,  return the vector $π=p_1,...,p_k$ of their  [softmax](https://en.wikipedia.org/wiki/Softmax_function) probabilities,  as per

$p_i=\frac{\textrm{e}^{c_i}}{\sum_{i=1}^{k}\textrm{e}^{c_i}}$.

**Examples**

```julia
χ=[1.0, 2.3, 0.4, 5.0]
π=softmax(χ)
```
