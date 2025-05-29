```
RunReport(args...; kwargs...) -> Manager
```

Creates profiles for functions of runtime and memory consumption for different input sizes.

# Arguments

  * `funcarray::Array{Base.Callable}` or `func::Base.Callable`: the function(s) to profile
  * `genfunc::Base.Callable`: function that generates inputs of different sizes for

the function(s)

  * `insizes`: iterable of integers that are used as inputs for `genfunc`

# Keywords

  * `seconds::Number`: parameter of `@benchmarkable`
  * `samples::Integer`: parameter of `@benchmarkable`
