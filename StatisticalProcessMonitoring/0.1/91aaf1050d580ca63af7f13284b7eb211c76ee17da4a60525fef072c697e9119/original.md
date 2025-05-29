```
combinedCL(CH::ControlChart; kw...)
```

Applies the bisection algorithm to find the control limit of a control chart without modifying the control chart object `CH`. The control limit upper bound `hmax` for the bisection algorithm is found using the stochastic approximation algorithm of Capizzi and Masarotto (2016). See the documentation of `combinedCL!` for more information about the algorithm and keyword arguments.

### Keyword arguments

  * See the documentation of `combinedCL!` for a list of keyword arguments.

### Returns

  * A `NamedTuple` containing the estimated control limit `h`, the total number of iterations `iter`, and information `status` about the convergence of the algorithm.

### References

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.
  * Capizzi, G., & Masarotto, G. (2016). Efficient control chart calibration by simulated stochastic approximation. IIE Transactions, 48(1), 57-65. https://doi.org/10.1080/0740817X.2015.1055392
