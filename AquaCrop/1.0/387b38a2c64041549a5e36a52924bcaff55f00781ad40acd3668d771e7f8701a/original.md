```
write_out_csv(file, cropfield::AquaCropField, field::Symbol; kwargs...)
```

Writes the dataframe of `cropfield.outputs[field]` on `file` using csv format.

This is a wraper of `CSV.write` that removes the units, the keywords `kwargs` are passed to `CSV.write`.

If the `digits` keyword argument is provided, it rounds to the specified number of digits after the decimal place, otherwise uses default of `digits=4`.
