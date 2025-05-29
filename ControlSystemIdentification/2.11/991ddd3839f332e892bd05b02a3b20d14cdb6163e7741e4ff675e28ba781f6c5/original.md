```
modelfit(y, yh)
```

Compute the model fit of `yh` to `y` as a percentage, sometimes referred to as the normalized root mean square error (NRMSE).

$$
\text{modelfit}(y, \hat{y}) = 100 \left(1 - \frac{\sqrt{\text{SSE}(y - \hat{y})}}{\sqrt{\text{SSE}(y - \bar{y})}}\right)
$$

An output of 100 indicates a perfect fit, an output of 0 indicates that the fit is no better than the mean if the data. Negative values are possible if the prediction is worse than predicting the mean of the data.

See also [`rms`](@ref), [`sse`](@ref), [`mse`](@ref), [`fpe`](@ref), [`aic`](@ref).
