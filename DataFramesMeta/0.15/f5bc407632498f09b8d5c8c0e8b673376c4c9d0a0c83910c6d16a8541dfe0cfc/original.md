```
@with(d, expr)
```

`@with` allows DataFrame columns keys to be referenced as symbols.

### Arguments

  * `d` : an AbstractDataFrame type
  * `expr` : the expression to evaluate in `d`

### Details

`@with` works by parsing the expression body for all columns indicated by symbols (e.g. `:colA`). Then, a function is created that wraps the body and passes the columns as function arguments. This function is then called. Operations are efficient because:

  * A pseudo-anonymous function is defined, so types are stable.
  * Columns are passed as references, eliminating DataFrame indexing.

The following

```julia
@with(d, :a .+ :b .+ 1)
```

becomes

```julia
tempfun(a, b) = a .+ b .+ 1
tempfun(d[!, :a], d[!, :b])
```

If an expression is wrapped in `^(expr)`, `expr` gets passed through untouched. If an expression is wrapped in  `$(expr)`, the column is referenced by the variable `expr` rather than a symbol.

If the expression provide to `@with` begins with `@byrow`, the function created by the `@with` block is broadcasted along the columns of the data frame.

### Examples

```jldoctest
julia> using DataFramesMeta

julia> y = 3;

julia> df = DataFrame(x = 1:3, y = [2, 1, 2]);

julia> x = [2, 1, 0];

julia> @with(df, :y .+ 1)
3-element Vector{Int64}:
 3
 2
 3

julia> @with(df, :x + x)
3-element Vector{Int64}:
 3
 3
 3

julia> @with df begin
            res = 0.0
            for i in 1:length(:x)
                res += :x[i] * :y[i]
            end
            res
        end
10.0

julia> @with(df, df[:x .> 1, ^(:y)]) # The ^ means leave the :y alone
2-element Vector{Int64}:
 1
 2

julia> colref = :x;

julia> @with(df, :y + $colref) # Equivalent to df[!, :y] + df[!, colref]
3-element Vector{Int64}:
 3
 3
 5

julia> @with df @byrow :x * :y
3-element Vector{Int64}:
 2
 2
 6

```

!!! note
    `@with` creates a function, so the scope within `@with` is a local scope. Variables in the parent can be read. Writing to variables in the parent scope differs depending on the type of scope of the parent. If the parent scope is a global scope, then a variable cannot be assigned without using the `global` keyword. If the parent scope is a local scope (inside a function or let block for example), the `global` keyword is not needed to assign to that parent scope.


!!! note
    Using `AsTable` inside `@with` block is currently not supported.

