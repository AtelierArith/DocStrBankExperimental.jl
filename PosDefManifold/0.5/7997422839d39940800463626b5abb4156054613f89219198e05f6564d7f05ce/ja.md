```
softmax(χ::Vector{T}) where T<:Real
```

非負のスコア $χ=c_1,...,c_k$ の実ベクトルが与えられたとき、次のようにその [softmax](https://en.wikipedia.org/wiki/Softmax_function) 確率のベクトル $π=p_1,...,p_k$ を返します。

$$
p_i=\frac{\textrm{e}^{c_i}}{\sum_{i=1}^{k}\textrm{e}^{c_i}}
$$

。

**例**

```julia
χ=[1.0, 2.3, 0.4, 5.0]
π=softmax(χ)
```
