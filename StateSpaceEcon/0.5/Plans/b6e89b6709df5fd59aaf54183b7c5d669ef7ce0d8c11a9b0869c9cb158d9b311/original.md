```
exportplan(plan; options)
exportplan(file, plan; options)
```

Display the plan or save it in a text file.

### Options

  * `alphabetical=false` - set to `true` to sort the variables. By default variables will be listed in the same order as in the model.
  * `exog_mark="X"` - a short string (ideally 1 character) to mark exogenous values.
  * `endo_mark="-"` - a short string (ideally 1 character) to mark endogenous values.
  * `delim=" "` - delimiter. Use `","`` to make it a CSV file.

See also [`importplan`](@ref)
