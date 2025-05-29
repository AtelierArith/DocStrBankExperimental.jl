```
bootstrapCL(CH::ControlChart; kw...)
```

Applies the bisection algorithm on simulated run length paths to find the control limit of a control chart without modifying the control chart object `CH`.

### Keyword arguments

See the documentation of `bootstrapCL!` for more information about the algorithm and keyword arguments.

### Returns

  * A `NamedTuple` containing the estimated control limit `h`, the total number of iterations `iter`, and information `status` about the convergence of the algorithm.

### References

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.
