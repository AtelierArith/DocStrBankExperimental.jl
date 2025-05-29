```
recod_catbydict(x, dict)
```

Recode a categorical variable to dictionnary levels.

  * `x` : Categorical variable (n) to replace.
  * `dict` : Dictionary giving the correpondances between the old    and new levels.

See examples.

## Examples

```julia
using Jchemo

dict = Dict("a" => 1000, "b" => 1, "c" => 2)
x = ["c" ; "c" ; "a" ; "a" ; "a"]
recod_catbydict(x, dict)

x = ["c" ; "c" ; "a" ; "a" ; "a" ; "e"]
recod_catbydict(x, dict)
```
