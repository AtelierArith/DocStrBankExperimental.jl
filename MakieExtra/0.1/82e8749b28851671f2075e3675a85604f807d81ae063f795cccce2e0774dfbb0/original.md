```
EngTicks(kind=:number; suffix="", digits=0, space=true)
```

Tick formatter that uses the engineering notation: like the scientific notation, but the exponent is always a multiple of 3. E.g., `10000` becomes `10×10³` when `kind=:number` and `10k` when `kind=:symbol`.

## Arguments

  * `kind`: The kind of engineering notation to use. Can be `:number` or `:symbol`
  * `suffix`: A string to append to the tick labels, e.g. `suffix="m"` could result in labels like "10 km"
  * `digits`: The number of decimal places to display (experimental, may be removed if there are no usecases)
  * `space`: Whether to include a space between the number and the suffix
