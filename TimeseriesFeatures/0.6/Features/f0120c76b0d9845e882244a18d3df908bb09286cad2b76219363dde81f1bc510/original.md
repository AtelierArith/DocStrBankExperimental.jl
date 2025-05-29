```
𝑓 = Feature([;] method::Function, name=Symbol(method), keywords="", description="")
```

Construct a `Feature`, which is a function annotated with a `name`, `keywords` and short `description`. Features can be called as functions while `getname(𝑓)`, `getkeywords(𝑓)` and `getdescription(𝑓)` can be used to access the annotations. The function should have at minimum a method for `AbstractVector`. The method on vectors will be applied column-wise to `Matrix` inputs, regardless of the function methods defined for `Matrix`.

# Examples

```julia
𝑓 = Feature(sum, :sum, ["distribution"], "Sum of time-series values")
𝑓(1:10) # == sum(1:10) == 55
getdescription(𝑓) # "Sum of time-series values"
```
