```
p = characteristic_polynomial(g_ol)
```

Determine the characteristic polynomial associated with open loop transfer function `g_ol`.

The characteristic polynomial is $1+g_{ol}(s)$. The roots of the characteristic polynomial determine the character of the response of the closed loop system to bounded inputs.

# Arguments

  * `g_ol::TransferFunction`: open loop transfer function

# Returns

a polynomial of type `Polynomial`

# Example

```jldoctest
g_ol = 4 / (s + 3) / (s + 2) / (s + 1)
characteristic_polynomial(g_ol)
# output
Polynomial(10.0 + 11.0*s + 6.0*s^2 + 1.0*s^3)
```
