```
saCL(CH::ControlChart[; rlsim::Function, kw...])
```

Applies the stochastic approximation algorithm of Capizzi and Masarotto (2016) without modifying the control chart object `CH`.

### Keyword arguments

See the documentation of `saCL!` for more information about the algorithm and the keyword arguments.

### Returns

  * A `NamedTuple` containing the estimated control limit `h`, the total number of iterations `iter`, and information `status` about the convergence of the algorithm.

### References

  * Capizzi, G., & Masarotto, G. (2016). "Efficient Control Chart Calibration by Simulated Stochastic Approximation". IIE Transactions 48 (1). https://doi.org/10.1080/0740817X.2015.1055392.
