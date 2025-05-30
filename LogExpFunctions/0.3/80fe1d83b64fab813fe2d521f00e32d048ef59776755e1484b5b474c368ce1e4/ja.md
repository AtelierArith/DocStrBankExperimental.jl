```julia
logistic(x)

```

[ロジスティック](https://en.wikipedia.org/wiki/Logistic_function)シグモイド関数は、実数を区間$[0,1]$の値にマッピングします。

$$
\sigma(x) = \frac{1}{e^{-x} + 1} = \frac{e^x}{1+e^x}.
$$

その逆関数は[`logit`](@ref)関数です。
