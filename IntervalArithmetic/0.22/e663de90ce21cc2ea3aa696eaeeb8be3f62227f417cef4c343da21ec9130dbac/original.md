```
I"str"
```

Create an interval by parsing the string `"str"`; this is semantically equivalent to `parse(Interval{[DEFAULT BOUND TYPE]}, "str")`.

# Examples

```jldoctest
julia> setdisplay(:full);

julia> I"[3, 4]"
Interval{Float64}(3.0, 4.0, com)

julia> I"0.1"
Interval{Float64}(0.09999999999999999, 0.1, com)

julia> in_interval(1//10, I"0.1")
true
```
