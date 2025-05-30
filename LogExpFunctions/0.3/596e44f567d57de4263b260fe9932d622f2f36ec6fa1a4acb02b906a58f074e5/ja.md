```julia
logit(x)

```

[logit](https://en.wikipedia.org/wiki/Logit)またはロジット変換は、次のように定義されます。

$$
\operatorname{logit}(x) = \log\left(\frac{x}{1-x}\right)
$$

$$
0 < x < 1
$$

の範囲で。

その逆は[`logistic`](@ref)関数です。
