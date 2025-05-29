```
label_number(;precision=2, scale=1, prefix="", suffix="", decimal_mark=".", comma_mark=",", style_positive=:none, style_negative=:hyphen, kwargs...)
```

Format numeric values as strings with various styling options.

# Arguments

  * `precision`: Number of decimal places.
  * `scale`: Scaling factor applied to the numbers before formatting.
  * `prefix`: String to prepend to the number.
  * `suffix`: String to append to the number.
  * `decimal_mark`: Character to use as the decimal point.
  * `comma_mark`: Character to use as the thousands separator.
  * `style_positive`: Style for positive numbers (:none, :plus, :space).
  * `style_negative`: Style for negative numbers (:hyphen, :parens).
  * `kwargs`: Additional keyword arguments passed on to `format` from `Format.jl`

# Examples

```julia
labeler = label_number(precision=0, suffix="kg")
labeler([1500.12, -2000.12]) # ["1,500kg", "-2,000kg"]
```
