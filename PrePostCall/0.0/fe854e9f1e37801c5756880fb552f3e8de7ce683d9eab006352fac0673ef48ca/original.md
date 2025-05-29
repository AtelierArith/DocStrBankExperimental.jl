```
@post function name ...
```

Create a macro `@name [[variable] variable ...] function other ...` for inserting a call to `name` after each call to `other`.

`variable` defines the variable names passed to `name`. If `variable` is omitted, `name` is called on the return argument of `other`. If `variable` is used, the call to `other` is inserted before each `return`, or if non present, as last expression in `other`. If multiple variables are given `name` is called on each of them, for example:

  * `@name x y z` is just a short notation for `@name x @name y @name z` and calls `name(x)`, `name(y)`, `name(z)`
  * `@name x,y,z` calls `name(x,y,z)`

# Examples

```jldoctest
julia> @post function nonzero(x::Int)
           @assert x!=0
       end
@nonzero (macro with 2 methods)

julia> @nonzero function foo(x::Int,y::Int)
           x*y
       end
foo (generic function with 1 method)

julia> foo(1,2)
2

julia> foo(1,0)
ERROR: AssertionError: x != 0

julia> @nonzero @nonzero a function foo(x::Int,y::Int)
           a = x-1
           return a*y
       end
foo (generic function with 1 method)

julia> foo(1,2)
ERROR: AssertionError: x != 0
```

Failes because `a` must be nonzero

```jldoctest
julia> foo(2,2)
2

julia> foo(2,0)
ERROR: AssertionError: x != 0
```

Failes because the return value must be nonzero
