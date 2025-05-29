```
BigFixedPoint(v,p)
```

Create a mutable struct that contains an integer value(v) with integer decimal places(p)

The value is always an integer. The p (precision) value determins how many decimal places are represented.

In the case that v is a float type, the number is rounded to p digits and then scaled to 10^p

# Examples

```
x = BigFixedPoint(4125,2)
println(x)
41.25
println(x * 2)
82.50 
```

All math operators are supported as well as most math functions. When calling math functions the number is converted to a BigFloat and then back to BigFixedPoint type. The number of digits are preserved. When types with mixed precision are mixed all operands and the result are widened to the maximum precision  of all operands. The return type of equations and math functions are almost always goint to be a BigFixedPoint type value.
