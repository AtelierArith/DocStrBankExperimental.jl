```
@filter func
@filter alias func
```

This macro registers `func` into OteraEngine, then the function is availble as a filter. The form of `func` should be normal or one-line definition but not anonymous. And you can also define filter with alias.

# Example

```julia-repr
julia> @filter function greet(x)
            return x * "Hello"
        end
julia> @filter hello function greet(x)
            return x * "Hello"
        end
julia> @filter say_twice(x) = x*x
julia> @filter double say_twice(x) = x*x
```

After define filters like this, you can use them as `greet`, `hello`, `say_twice`, `double`.
