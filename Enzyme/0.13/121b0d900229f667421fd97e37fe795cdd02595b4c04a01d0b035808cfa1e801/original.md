```
autodiff(::Function, ::Mode, args...)
```

Specialization of [`autodiff`](@ref) to handle do argument closures.

```jldoctest

autodiff(Reverse, Active(3.1)) do x
  return x*x
end

# output
((6.2,),)
```
