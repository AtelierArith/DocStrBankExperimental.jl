```
parse(::FixedPoint, s)
```

This function will parse a string and attempt to create FixedPoint type from it. It will attempt to determine the precision from the number of digits to the right of the decimal point.

# Examples

```
x = parse(FixedPoint, "41.25")
println(x)
41.25
println(x * 2)
82.50 
```
