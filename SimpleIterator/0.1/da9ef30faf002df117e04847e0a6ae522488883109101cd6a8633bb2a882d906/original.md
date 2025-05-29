```
@iterfn
```

Define a iterator for a type. The type should have a function named [`iterator`](@ref) which returns a iterator. After the macro is called, iteration over the type will automatically becomes iteration over the iterator.

# Arguments

  * `fundef`: function definition to be decorated, the function name should be `iterator`.

# Example

```julia
struct MyType
    data::Vector{Int}
end

@iterfn iterator(x::MyType) = x.data

for i in MyType([1, 2, 3])
    println(i)
end
```
