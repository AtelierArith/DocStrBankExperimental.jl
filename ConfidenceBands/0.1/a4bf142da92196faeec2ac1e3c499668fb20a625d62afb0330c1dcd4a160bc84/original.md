```
confint(cb::SuptCVBootBand, θ0::AbstractVector, draws::AbstractMatrix; level::Real=0.9)
```

Compute a sup-t confidence band with critical-value-based bootstrap implementation based on Montiel Olea and Plagborg-Møller (2019) Algorithm 3 in appendix. `θ0` is a vector of point estimates to be used as the middle points of the band. The bootstrap `draws` of point estimates need to be in a matrix with each column being a vector of point estimates from the same draw. In addition to the lower and upper bounds, the critical value is returned as the third object.

# References

  * Montiel Olea, José Luis and Mikkel Plagborg-Møller. 2019. "Simultaneous Confidence Bands: Theory, Implementation, and an Application to SVARs." Journal of Applied Econometrics 34 (1): 1-17.
