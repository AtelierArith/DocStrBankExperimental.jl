```
PlackettCopula{P}
```

Fields:     - θ::Real - parameter

Constructor

```
PlackettCopula(θ)
```

The bivariate Plackett Copula parameterized by $\theta > 0$ The [Plackett](https://www.cambridge.org/core/books/abs/copulas-and-their-applications-in-water-resources-engineering/plackett-copula/2D407DAB691623AB52CF74044B42C61F). It is constructed as:  

$$
C(u_1,u_2) = \frac{1}{2}\eta^{-1}(1+\eta(u_1+u_2)-((1+\eta(u_1+u_2))^2 - 4\theta \eta u_1 u_2)^{1/2}) 
$$

where $\eta)=\theta-1.$

It has a few special cases: 

  * When θ = ∞, is is the MCopula (Upper Frechet-Hoeffding bound)
  * When θ = 1, it is the IndependentCopula
  * When θ = 0, is is the WCopula (Lower Frechet-Hoeffding bound)

References:

  * [joe2014](@cite) Joe, H. (2014). Dependence modeling with copulas. CRC press, Page.164
  * [johnson1987multivariate](@cite) Johnson, Mark E. Multivariate statistical simulation: A guide to selecting and generating continuous multivariate distributions. Vol. 192. John Wiley & Sons, 1987. Page 193.
  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006. Exercise 3.38.
