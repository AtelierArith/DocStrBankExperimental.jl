```
MOCopula{P}
```

Fields:

```
- λ1::Real - parameter
- λ2::Real - parameter
- λ12::Real - parameter
```

Constructor

```
MOCopula(θ)
```

The bivariate Marshall-Olkin copula is parameterized by $\lambda_i \in [0,\infty), i = 1, 2, \{1,2\}$. It is an Extreme value copula with Pickands dependence function: 

$$
A(t) = \frac{\lambda_1 (1-t)}{\lambda_1 + \lambda_{1,2}} + \frac{\lambda_2 t}{\lambda_2 + \lambda_{1,2}} + \lambda_{1,2}\max\left \{\frac{1-t}{\lambda_1 + \lambda_{1,2}}, \frac{t}{\lambda_2 + \lambda_{1,2}}  \right \} 
$$

References:

  * [Mai2017](@cite) Simulating copulas: stochastic models, sampling algorithms, and applications. 2017.
