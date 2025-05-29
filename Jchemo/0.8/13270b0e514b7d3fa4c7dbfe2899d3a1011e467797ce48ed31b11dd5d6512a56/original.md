```
recod_catbyind(x, lev)
```

Recode a categorical variable to indexes of levels.

  * `x` : Categorical variable (n) to replace.
  * `lev` : Vector containing categorical levels.

See examples.

*Warning*: The levels in `x` must be contained in `lev`.

## Examples

```julia
using Jchemo

lev = ["EHH" ; "FFS" ; "ANF" ; "CLZ" ; "CNG" ; "FRG" ; "MPW" ; "PEE" ; "SFG" ; "SFG" ; "TTS"]
slev = mlev(lev)
[slev 1:length(slev)] 
x = ["EHH" ; "TTS" ; "FRG" ; "EHH"]
recod_catbyind(x, lev)
```
