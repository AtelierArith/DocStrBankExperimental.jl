```
@eachrow!(df, body)
```

Act on each row of a data frame in-place, similar to

```
for row in eachrow(df)
    ... # Actions that modify `df`.
end
```

Includes support for control flow and `begin end` blocks. Since the "environment" induced by `@eachrow! df` is implicitly a single row of `df`, use regular operators and comparisons instead of their elementwise counterparts as in `@with`. Note that the scope within `@eachrow!` is a hard scope.

`eachrow!` also supports special syntax for allocating new columns. The syntax `@newcol x::Vector{Int}` allocates a new uninitialized column `:x` with an `Vector` container with eltype `Int`.This feature makes it easier to use `eachrow` for data transformations. `_N` is introduced to represent the number of rows in the data frame, `_DF` represents the `dataframe` including added columns, and `row` represents the index of the current row.

Changes to the rows directly affect `df`. The operation will modify the data frame in place. See [`@eachrow`](@ref) which employs the same syntax but allocates a fresh data frame.

Like with `@transform!`, `@eachrow!` supports the use of `$` to work with column names stored as variables. Using `$` with a multi-column selector, such as a `Vector` of `Symbol`s, is currently unsupported.

`@eachrow!` is a thin wrapper around a `for`-loop. As a consequence, inside an `@eachrow!` block, the reserved-word arguments `break` and `continue` function the same as if written in a `for` loop. Rows unaffected by `break` and `continue` are unmodified, but are still present in modified. Also because `@eachrow!` is a `for`-loop, re-assigning global variables inside an `@eachrow` block is discouraged.

### Arguments

  * `df` : an `AbstractDataFrame`
  * `expr` : expression operated on row by row

### Returns

The modified `AbstractDataFrame`.

### Examples

```julia
julia> using DataFramesMeta

julia> df = DataFrame(A = 1:3, B = [2, 1, 2]);

julia> let x = 0
            @eachrow! df begin
                if :A + :B == 3
                    x += 1
                end
            end  #  This doesn't work without the let
            x
        end
2

julia> df2 = copy(df);

julia> @eachrow! df2 begin
           if :A > :B
               :A = 0
           end
       end;

julia> df2
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      2
   2 │     0      1
   3 │     0      2

julia> df2 = copy(df);

julia> @eachrow! df2 begin
           @newcol :colX::Vector{Float64}
           :colX = :B == 2 ? pi * :A : :B
       end
3×3 DataFrame
 Row │ A      B      colX
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      2  3.14159
   2 │     2      1  1.0
   3 │     3      2  9.42478

julia> varA = :A; varB = :B;

julia> df2 = copy(df);

julia> @eachrow! df2 begin
           @newcol :colX::Vector{Float64}
           :colX = $varB == 2 ? pi * $varA : $varB
       end
3×3 DataFrame
 Row │ A      B      colX
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      2  3.14159
   2 │     2      1  1.0
   3 │     3      2  9.42478

julia> x = [1, 1, 1];

julia> @eachrow! df begin
           x[row] = :A
       end;

julia> x
3-element Vector{Int64}:
 1
 2
 3

julia> @eachrow! df begin
           @newcol :m::Vector{Float64}
           :m = mean(_DF[:, row])
       end
3×3 DataFrame
 Row │ A      B      m
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      2  2.0
   2 │     2      1  1.66667
   3 │     3      2  1.22222

julia> @eachrow! df begin
           :A == 2 && continue
           println(:A)
       end;
1
3
```
