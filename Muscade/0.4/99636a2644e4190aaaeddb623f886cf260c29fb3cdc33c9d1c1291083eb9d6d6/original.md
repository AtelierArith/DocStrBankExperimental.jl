```
X = variate{P,N}(x)
```

where `typeof(x)<:SVector{N}`, create a `SVector` of automatic differentiation objects of precedence `P`.    

```
X = variate{P}(x)
```

where `typeof(x)<:Real`, create an object of precedence `P`.    

See also: [`constants`](@ref), [`δ`](@ref), [`value`](@ref), [`∂`](@ref), [`VALUE`](@ref), [`value_∂`](@ref)
