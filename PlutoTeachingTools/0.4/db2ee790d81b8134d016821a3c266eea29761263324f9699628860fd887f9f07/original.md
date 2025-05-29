```
Columns(cols...; widths, gap)
```

Displays (any number of) columns nicely in Pluto. 

  * `widths` should sum to 100
  * `gap` in percent

### Examples

```julia
# three columns
Columns(
    almost(md"here"),
    almost(md"there"),
    md"bla bla bla"
)

# two columns with customization
Columns(
    almost(md"here"), almost(md"there"), 
    widths = [40, 60], gap = 2
)
```
