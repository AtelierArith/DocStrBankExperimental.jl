```
PowerGeneralizedWeibull(σ,ν,γ)
```

The Power Generalised Weibull (PGW) distribution is a three-parameter distribution with support on ${\mathbb R}_+$. The corresponding hazard function can accommodate bathtub, unimodal and monotone (increasing and decreasing) hazard shapes. The PGW distribution has become popular in survival analysis given the tractability of its hazard and survival functions. 

The `PowerGeneralizedWeibull(σ,ν,γ)` distribution, with scale `σ`, shape `ν` (nu) and second shape `γ` has probability density function 

$$
f(t;σ,ν,γ) = \dfrac{ν}{γ σ^ν}t^{ν-1} \left[ 1 + \left(\dfrac{t}{σ}\right)^ν\right]^{\left(\frac{1}{γ}-1\right)} \exp\left\{ 1- \left[ 1 + \left(\dfrac{t}{σ}\right)^ν\right]^{\frac{1}{γ}}
\right\}.
$$

References: 

  * [nikulin:2009](@cite) Nikulin, M. and Haghighi, F. On the power generalized Weibull family: model for cancer censored data. Metron – International Journal of Statistics, 2009
