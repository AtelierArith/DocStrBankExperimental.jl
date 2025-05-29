```
autodiff(::Function, ::Mode, args...)
```

[`autodiff`](@ref) の特殊化で、do引数クロージャを処理します。

```jldoctest

autodiff(Reverse, Active(3.1)) do x
  return x*x
end

# output
((6.2,),)
```
