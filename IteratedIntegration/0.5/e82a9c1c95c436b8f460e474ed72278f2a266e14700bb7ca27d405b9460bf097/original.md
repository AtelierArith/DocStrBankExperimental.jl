```
ProductLimits(lims::AbstractIteratedLimits...)
```

Construct a collection of limits which yields the first limit followed by the second, and so on. The inner limits are not allowed to depend on the outer ones. The outermost variable of integration should be placed first, i.e. $\int_{\Omega} \int_{\Gamma}$ should be `ProductLimits(Ω, Γ)`. Although changing the order of the limits should not change the results, putting the shortest limits first may save `nested_quadgk` some work.
