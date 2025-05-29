```
KGL08(S::T) where {T<:NamedTuple}
```

$$
\beta_t = \frac{L+R}{(2S + L + R)}
$$

このメソッドは[Poisot2022Dissimilarity](@citet)で使用されており、多くの望ましい特性を持っています。デフォルトとしての使用を提案します。

###### 参考文献

[Wilson1984Measuring](@citet*)
