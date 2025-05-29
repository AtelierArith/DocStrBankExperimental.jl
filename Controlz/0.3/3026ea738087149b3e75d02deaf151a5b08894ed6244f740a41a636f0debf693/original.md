```
o = system_order(tf::TransferFunction)
```

return the order of the numerator and denominator of the transfer function `tf`.

use [`pole_zero_cancellation`](@ref) first if you wish to cancel poles and zeros that are equal before determining the order.

# returns

`o::Tuple{Int, Int}`: (order of numerator, order of denominator)

# examples

```jldoctest
g = 1 / (s + 1)
system_order(g)
# output 
(0, 1)

g = (s + 1) / ((s + 2) * (s + 3))
system_order(g)
# output
(1, 2)
```
