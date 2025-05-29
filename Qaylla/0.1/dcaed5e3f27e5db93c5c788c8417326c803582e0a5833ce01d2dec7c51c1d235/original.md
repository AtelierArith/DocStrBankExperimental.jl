```
cubic_splines(x_data,y_data)::Function
```

Computes the cubic splines  interpolation polynomial

## Arguments

  * `x_data`: The xᵢ values for i=1,2...n
  * `y_data`: The f(xᵢ) values for i=1,2...n

## Return

  * `p::Function`: The cubic splines interpolation polynomial

## Example

```jldoctest
using Qaylla

x=0:pi/4:3*pi
y=sin.(x)
p=cubic_splines(x,y)
p(2.5)

# output

0.59842733419271

```
