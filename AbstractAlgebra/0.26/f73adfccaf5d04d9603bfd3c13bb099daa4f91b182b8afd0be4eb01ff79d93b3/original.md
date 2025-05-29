```
@attr [RetType] funcdef
```

This macro is applied to the definition of a unary function, and enables caching ("memoization") of its return values based on the argument. This assumes the argument supports attribute storing (see [`@attributes`](@ref)) via [`get_attribute!`](@ref).

The name of the function is used as name for the underlying attribute.

Effectively, this turns code like this:

```julia
@attr function RetType myattr(obj::Foo)
   # ... expensive computation
   return result
end
```

into something essentially equivalent to this:

```julia
function myattr(obj::Foo)
  return get_attribute!(obj, :myattr) do
    # ... expensive computation
    return result
  end::RetType
end
```

# Examples

```jldoctest; setup = :(using AbstractAlgebra)
julia> @attributes mutable struct Foo
           x::Int
           Foo(x::Int) = new(x)
       end;

julia> @attr Int function myattr(obj::Foo)
                println("Performing expensive computation")
                return factorial(obj.x)
             end;

julia> obj = Foo(5);

julia> myattr(obj)
Performing expensive computation
120

julia> myattr(obj) # second time uses the cached result
120

```
