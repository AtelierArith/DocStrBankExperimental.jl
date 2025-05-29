```
@TryCatch YourException begin
  your_code
end
```

A version of [`@Try`](@ref) which catches only specific errors. Every other orrer will be `rethrown`.

It translates to

```julia
try
  r = your_code
  Identity(r)
catch exc
  if exc isa YourException
    Const(Thrown(exc, Base.catch_stack()))
  else
    rethrow()
  end
end
```
