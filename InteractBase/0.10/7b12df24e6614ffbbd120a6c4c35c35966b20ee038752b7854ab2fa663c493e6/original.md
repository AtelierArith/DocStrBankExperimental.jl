```
dropdown(options::AbstractDict;
         value = first(values(options)),
         label = nothing,
         multiple = false)
```

A dropdown menu whose item labels are the keys of options. If `multiple=true` the observable will hold an array containing the values of all selected items e.g. `dropdown(OrderedDict("good"=>1, "better"=>2, "amazing"=>9001))`

`dropdown(values::AbstractArray; kwargs...)`

`dropdown` with labels `string.(values)` see `dropdown(options::AbstractDict; ...)` for more details
