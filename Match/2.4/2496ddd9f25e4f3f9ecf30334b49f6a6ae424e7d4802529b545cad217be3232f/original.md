```
@match pattern = value
@match value begin
    pattern1 => result1
    pattern2 => result2
    ...
end
```

Match a given value to a pattern or series of patterns.

This macro has two forms.  In the first form

```
@match pattern = value
```

Return the value if it matches the pattern, and bind any pattern variables. Otherwise, throw `MatchFailure`.

In the second form

```
@match value begin
    pattern1 => result1
    pattern2 => result2
    ...
end
```

Return `result` for the first matching `pattern`. If there are no matches, throw `MatchFailure`.

To avoid a `MatchFailure` exception, write the `@match` to handle every possible input. One way to do that is to add a final case with the wildcard pattern `_`.

# See Also

See also

  * `@match_fail`
  * `@match_return`
  * `@ismatch`

# Patterns:

The following syntactic forms can be used in patterns:

  * `_` matches any value
  * `x` (an identifier) matches any value and binds it to the variable `x`
  * `T(x,y,z)` matches structs of type `T` with fields matching patterns `x,y,z`
  * `T(y=p)` matches structs of type `T` whose `y` field matches pattern `p`
  * `(;x,y,z)` matches values with fields `x,y,z` binding to variables `x,y,z`
  * `(;x=p)` matches values with field `x` matching pattern `p`; does not bind `x`.
  * `(;x::T)` matches values with field `x` matching pattern `::T`; also binds the field to `x`
  * `[x,y,z]` matches `AbstractArray`s with 3 entries matching `x,y,z`
  * `(x,y,z)` matches `Tuple`s with 3 entries matching `x,y,z`
  * `[x,y...,z]` matches `AbstractArray`s with at least 2 entries, where `x` matches the first entry, `z` matches the last entry and `y` matches the remaining entries.
  * `(x,y...,z)` matches `Tuple`s with at least 2 entries, where `x` matches the first entry, `z` matches the last entry and `y` matches the remaining entries.
  * `::T` matches any subtype (`isa`) of type `T`
  * `x::T` matches any subtype (`isa`) of T that also matches pattern `x`
  * `x || y` matches values which match either pattern `x` or `y` (only variables which exist in both branches will be bound)
  * `x && y` matches values which match both patterns `x` and `y`
  * `x, if condition end` matches only if `condition` is true (`condition` may use any variables that occur earlier in the pattern eg `(x, y, z where x + y > z)`)
  * `x where condition` An alternative form for `x, if condition end`
  * `if condition end` A boolean computed pattern. `x && if condition end` is another way of writing `x where condition`.
  * `1` (a literal value) matches that value using `isequal`
  * `r"[a-z]*"` (a regular expression) matches strings that match the regular expression
  * `1:10` (a constant range) matches values in that range
  * Expressions can be interpolated in as constants via standard interpolation syntax `$(x)`.  Interpolations may use previously bound variables.

Patterns can be nested arbitrarily.

Repeated variables only match if they are equal (`isequal`). For example `(x,x)` matches `(1,1)` but not `(1,2)`.

# Examples

```julia-repl
julia> value=(1, 2, 3, 4)
(1, 2, 3, 4)

julia> @match (x, y..., z) = value
(1, 2, 3, 4)

julia> x
1

julia> y
(2, 3)

julia> z
4

julia> struct Foo
           x::Int64
           y::String
       end

julia> f(x) = @match x begin
           _::String => :string
           [a,a,a] => (:all_the_same, a)
           [a,bs...,c] => (:at_least_2, a, bs, c)
           Foo(x, "foo") where x > 1 => :foo
       end
f (generic function with 1 method)

julia> f("foo")
:string

julia> f([1,1,1])
(:all_the_same, 1)

julia> f([1,1])
(:at_least_2, 1, Int64[], 1)

julia> f([1,2,3,4])
(:at_least_2, 1, [2, 3], 4)

julia> f([1])
ERROR: MatchFailure([1])
...

julia> f(Foo(2, "foo"))
:foo

julia> f(Foo(0, "foo"))
ERROR: MatchFailure(Foo(0, "foo"))
...

julia> f(Foo(2, "not a foo"))
ERROR: MatchFailure(Foo(2, "not a foo"))
...
```
