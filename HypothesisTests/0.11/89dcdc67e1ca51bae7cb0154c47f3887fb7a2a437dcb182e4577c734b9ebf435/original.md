```
DieboldMarianoTest(e1::AbstractVector{<:Real}, e2::AbstractVector{<:Real}; loss=abs2, lookahead=1)
```

Perform the modified Diebold-Mariano test proposed by Harvey, Leybourne and Newbold of the null  hypothesis that the two methods have the same forecast accuracy. `loss` is the loss function described in Diebold, F.X. and Mariano, R.S. (1995) Comparing predictive accuracy. Journal of Business and  Economic Statistics, 13, 253-263. and `lookahead` is the number of steps ahead of the forecast.

# References

  * Diebold, F.X. and Mariano, R.S. (1995) Comparing predictive accuracy.  Journal of Business and Economic Statistics, 13, 253-263.
  * Harvey, D., Leybourne, S., & Newbold, P. (1997). Testing the equality of prediction  mean squared errors. International Journal of forecasting, 13(2), 281-291.
