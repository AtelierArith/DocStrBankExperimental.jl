```
tf = pole_zero_cancellation(tf, verbose=false, digits=8)
```

find (pole, zero) pairs such that pole = zero and return a new transfer function with those pairs cancelled. this is achieved by comparing the poles and zeros with `isapprox`, with poles and zeros rounded to  `digits` digits (also applies to reconstruction).

# arguments

  * `tf::TransferFunction`: the transfer function
  * `verbose::Bool=false`: print off which poles, zeros are cancelled.
  * `digits::Int`: number of digits to round poles and zeros to, for (i) cancelling and (ii) reconstruction.

# example

```jldoctest
pole_zero_cancellation(s * (s - 1) / (s * (s + 1)))
# output
1.0*s - 1.0
-----------
1.0*s + 1.0
```
