```
@byrow
```

Broadcast operations within DataFramesMeta.jl macros.

`@byrow` is not a "real" Julia macro but rather serves as a "flag" to indicate that the anonymous function created by DataFramesMeta to represent an operation should be applied "by-row".

If an expression starts with `@byrow`, either of the form `@byrow :y = f(:x)` in transformations or `@byrow f(:x)` in `@orderby`, `@subset`, and `@with`, then the anonymous function created by DataFramesMeta is wrapped in the `DataFrames.ByRow` function wrapper, which broadcasts the function so that it run on each row.

### Examples

```julia
julia> df = DataFrame(a = [1, 2, 3, 4], b = [5, 6, 7, 8]);

julia> @transform(df, @byrow :c = :a * :b)
4×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      5      5
   2 │     2      6     12
   3 │     3      7     21
   4 │     4      8     32

julia> @subset(df, @byrow :a == 1 ? true : false)
1×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      5
```

To avoid writing `@byrow` multiple times when performing multiple operations, it is allowed to use `@byrow` at the beginning of a block of operations. All transformations in the block will operate by row.

```julia
julia> @subset df @byrow begin
           :a > 1
           :b < 5
       end
1×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     2      4
```

### Comparison with `@eachrow`

To re-cap, the `@eachrow` macro roughly transforms

```julia
@eachrow df begin
    :a * :b
end
```

to

```julia
begin
    function tempfun(a, b)
        for i in eachindex(a)
            a[i] * b[i]
        end
    end
    tempfun(df.a, df.b)
    df
end
```

The function `*` is applied by-row. But the result of those operations is not stored anywhere, as with `for`-loops in Base Julia. Rather, `@eachrow` and `@eachrow!` return data frames.

Now consider `@byrow`. `@byrow` transforms

```julia
@with df @byrow begin
    :a * :b
end
```

to

```julia
tempfun(a, b) = a * b
tempfun.(df.a, df.b)
```

In contrast to `@eachrow`, `@with` combined with `@byrow` returns a vector of the broadcasted multiplication and not a data frame.

Additionally, transformations applied using `@eachrow!` modify the input data frame. On the contrary, `@byrow` does not update columns.

```julia
julia> df = DataFrame(a = [1, 2], b = [3, 4]);

julia> @with df @byrow begin
           :a = 500
       end
2-element Vector{Int64}:
 500
 500

julia> df
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4
```

### Comparison with `@.` and Base broadcasting

Base Julia provides the broadcasting macro `@.` and in many cases `@.` and `@byrow` will give equivalent results. But there are important deviations in behavior. Consider the setup

```julia
df = DataFrame(a = [1, 2], b = [3, 4])
```

  * Control flow. `@byrow` allows for operations of the form `if ... else` and `a ? b : c` to be applied by row. These expressions cannot be broadcasted in Base Julia. `@byrow` also allows for expressions of the form `a && b` and `a || b` to be applied by row, something that is not possible in Julia versions below 1.7.

```
julia> @with df @byrow begin
           if :a == 1
               5
           else
               10
           end
       end
2-element Vector{Int64}:
  5
 10

julia> @with df @. begin
           if :a == 1
               5
           else
               10
           end
       end # will error
```

  * Broadcasting objects that are not columns. `@byrow` constructs an anonymous function which accepts only the columns of the input data frame and broadcasts that function. Consequently, it does not broadcast referenced objects which are not columns.

```julia
julia> df = DataFrame(a = [1, 2], b = [3, 4]);
julia> @with df @byrow :x + [5, 6]
```

will error, because the `:x` in the above expression refers   to a scalar `Int`, and you cannot do `1 + [5, 6]`.

On the other hand

```julia
@with df @. :x + [5, 6]
```

will succeed, as `df.x` is a 2-element vector as is `[5, 6]`.

Because `ByRow` inside `transform` blocks does not internally   use broadcasting in all circumstances, in the rare instance   that a column in a data frame is a custom vector type that   implements custom broadcasting, this custom behavior will   not be called with `@byrow`.

  * Broadcasting expensive calls. In Base Julia, broadcasting evaluates calls first and then broadcasts the result. Because `@byrow` constructs an anonymous function and evaluates that function for every row in the data frame, expensive functions will be evaluated many times.

```julia
julia> function expensive()
           sleep(.5)
           return 1
       end;

julia> @time @with df @byrow :a + expensive();
  1.037073 seconds (51.67 k allocations: 3.035 MiB, 3.19% compilation time)

julia> @time @with df :a .+ expensive();
  0.539900 seconds (110.67 k allocations: 6.525 MiB, 7.05% compilation time)

```

This problem comes up when using the `@.` macro as well,   but can easily be fixed with `$`. Because `$` is currently   reserved for escaping column references, no solution currently exists with   `@byrow` or in DataFramesMeta.jl at large. The best solution is simply

```
@with df begin
    x = expensive()
    :a + x
end
```
