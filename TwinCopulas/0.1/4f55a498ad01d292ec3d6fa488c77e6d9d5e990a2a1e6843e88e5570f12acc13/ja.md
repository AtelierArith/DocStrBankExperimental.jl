```
PlackettCopula{P}
```

フィールド:     - θ::Real - パラメータ

コンストラクタ

```
PlackettCopula(θ)
```

二変量プラケットコピュラは $\theta > 0$ によってパラメータ化されます。[Plackett](https://www.cambridge.org/core/books/abs/copulas-and-their-applications-in-water-resources-engineering/plackett-copula/2D407DAB691623AB52CF74044B42C61F) に基づいて構築されています。  

$$
C(u_1,u_2) = \frac{1}{2}\eta^{-1}(1+\eta(u_1+u_2)-((1+\eta(u_1+u_2))^2 - 4\theta \eta u_1 u_2)^{1/2}) 
$$

ここで、$\eta)=\theta-1.$

いくつかの特別なケースがあります: 

  * θ = ∞ の場合、これは MCopula (上フレシェ-ホエフディング境界) です
  * θ = 1 の場合、これは IndependentCopula です
  * θ = 0 の場合、これは WCopula (下フレシェ-ホエフディング境界) です

参考文献:

  * [joe2014](@cite) Joe, H. (2014). Dependence modeling with copulas. CRC press, Page.164
  * [johnson1987multivariate](@cite) Johnson, Mark E. Multivariate statistical simulation: A guide to selecting and generating continuous multivariate distributions. Vol. 192. John Wiley & Sons, 1987. Page 193.
  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006. Exercise 3.38.
