```
tf = TransferFunction([1, 2], [3, 5, 8])
tf = TransferFunction([1, 2], [3, 5, 8], 3.0)
```

construct a transfer function representing a linear, time-invariant system.

# example

to construct the transfer function

$$
G(s) = \frac{4e^{-2.2s}}{2s+1}
$$

in Julia:

```jldoctest
tf = TransferFunction([4], [2, 1], 2.2)
# output
    4.0
----------- e^(-2.2*s)
2.0*s + 1.0
```

# attributes

  * `numerator::Polynomial{Float64, :s}`: the polynomial in the numerator of the transfer function
  * `denominator::Polynomial{Float64, :s}`: the polynomial in the denominator of the transfer function
  * `time_delay::Float64`: the associated time delay
