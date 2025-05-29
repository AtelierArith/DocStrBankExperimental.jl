```
@req(assert, msg)
@req assert msg
```

Check whether the assertion `assert` is true. If not, throw an `ArgumentError` with error message `msg`.

The macro `@req` takes two arguments: the first one is an assertion `assert` (an expression which returns a boolean) and a string `msg` corresponding to the desired error message to be returned whenever `assert` is false.

If the number of arguments is not 2, an `AssertionError` is raised.

# Examples

```jldoctest
julia> function req_test(x::Int)
       @req iseven(x) "x must be even"
       return div(x,2)
       end
req_test (generic function with 1 method)

julia> try req_test(3)
       catch e e
       end
ArgumentError("x must be even")

julia> try req_test(2)
       catch e e
       end
1

```
