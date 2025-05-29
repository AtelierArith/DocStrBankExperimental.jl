```
calculate_limit_gradient(CH::AbstractChart, rl::Real)
calculate_limit_gradient(nominal::ARL, rl)
calculate_limit_gradient(nominal::QRL, rl)
```

Calculate the gradient for the optimization of the control limit.

If the control chart `nominal` attribute is of type `ARL`, then the gradient is calculated according to Equation (9) of Capizzi and Masarotto (2016).

If the control chart `nominal` attribute is of type `QRL`, then the gradient is calculated using the recursion on page 280 of Capizzi and Masarotto (2009)

### References

Capizzi, G., & Masarotto, G. (2016). "Efficient Control Chart Calibration by Simulated Stochastic Approximation". IIE Transactions 48 (1). https://doi.org/10.1080/0740817X.2015.1055392.

Capizzi, G. & Masarotto, G. (2009) Bootstrap-based design of residual control charts, IIE Transactions, 41:4, 275-286, DOI: https://doi.org/10.1080/07408170802120059 
