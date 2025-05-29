```
@pre function name ...
```

Create a macro `@name [[variable] variable ...] function other ...` for inserting a call to `name` before each call to `other`.

`variable` defines the variable names passed to `name`. If `variable` is omitted the names of the attributes of `name` are used. If multiple variables are given `name` is called on each of them, for example:

  * `@name x y z` is just a short notation for `@name x @name y @name z` and calls `name(x)`, `name(y)`, `name(z)`
  * `@name x,y,z` calls `name(x,y,z)`

# Examples

```jldoctest
julia> @pre function nonzero(x::Int)
           @assert x!=0
       end
@nonzero (macro with 2 methods)

julia> @nonzero @nonzero y function foo(x::Int,y::Int)
           x+y
       end
foo (generic function with 1 method)
```

The outer `@nonzero` uses `x` as the attribute due to the function definition of `nonzero`.

```jldoctest
julia> foo(1,2)
3

julia> foo(1,0)
ERROR: AssertionError: x != 0

julia> foo(0,1)
ERROR: AssertionError: x != 0
```
