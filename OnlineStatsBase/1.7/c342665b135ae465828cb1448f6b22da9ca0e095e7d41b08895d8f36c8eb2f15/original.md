```
ExtremeValues(T = Float64, b=25)
```

Track the `b` smallest and largest values of a data stream (as well as how many times that value occurred).

# Example

```
o = ExtremeValues(Int, 3)

fit!(o, 1:100)

value(o).lo  # [1 => 1, 2 => 1, 3 => 1]

value(o).hi  # [98 => 1, 99 => 1, 100 => 1]
```
