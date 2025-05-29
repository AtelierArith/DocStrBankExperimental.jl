```
FixedPoint(v,p)
```

Create a mutable struct that contains an integer value(v) with integer decimal places(p)

The value is always an integer. The p (precision) value determins how many decimal places are represented.

In the case that v is a float type, the number is rounded to p digits and then scaled to 10^p

# Examples

```
x = FixedPoint(4125,2)
println(x)
41.25
println(x * 2)
82.50 
```

All math operators are supported as well as most math functions. When calling math functions the number is converted to a Float and then back to FixedPoint type. The number of digits are preserved. When types with mixed precision are mixed all operands and the result are widened to the maximum precision  of all operands. The return type of equations and math functions are almost always goint to be a FixedPoint type value.
