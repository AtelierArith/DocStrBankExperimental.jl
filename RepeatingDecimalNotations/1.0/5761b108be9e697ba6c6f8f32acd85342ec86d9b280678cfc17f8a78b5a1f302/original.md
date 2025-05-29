```
@rd_str
```

A string macro to create a rational number.

# Examples

```jldoctest
julia> r = rd"123.4(56)"  # 123.4565656...
61111//495

julia> rd"1.234r56e2"  # Other notations
61111//495

julia> rd"123.45656..."  # are also supported.
61111//495

julia> float(r)  # Check floating point number approximation.
123.45656565656566

julia> rd"0.(9)"  # 0.999... is equal to 1.
1//1

julia> rd"0.99(9)", rd"1", rd"1.000_000"  # The notation of repeating decimals is not unique.
(1//1, 1//1, 1//1)
```
