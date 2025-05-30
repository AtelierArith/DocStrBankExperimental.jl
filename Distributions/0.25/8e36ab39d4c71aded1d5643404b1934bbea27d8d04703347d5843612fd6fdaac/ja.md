```
Kumaraswamy(a, b)
```

*Kumaraswamy分布*は、形状パラメータ `a > 0` と `b > 0` を持ち、確率密度関数は次のようになります。

$$
f(x; a, b) = a b x^{a - 1} (1 - x^a)^{b - 1}, \quad 0 < x < 1
$$

これは、次の同一性によって[ベータ分布](@ref Beta)に関連しています：もし $X \sim \operatorname{Kumaraswamy}(a, b)$ ならば、$X^a \sim \operatorname{Beta}(1, b)$ です。特に、もし $X \sim \operatorname{Kumaraswamy}(1, 1)$ ならば、$X \sim \operatorname{Uniform}(0, 1)$ です。

外部リンク

  * [Kumaraswamy分布のWikipedia](https://en.wikipedia.org/wiki/Kumaraswamy_distribution)

参考文献

  * Kumaraswamy, P. (1980). A generalized probability density function for double-bounded random processes. Journal of Hydrology. 46(1-2), 79-88.
