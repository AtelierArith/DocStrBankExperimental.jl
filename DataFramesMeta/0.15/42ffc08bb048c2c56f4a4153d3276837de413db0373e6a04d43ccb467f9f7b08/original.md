```
@distinct!(d, args...)
```

In-place selection of unique rows in an `AbstractDataFrame`. Users should note that `@distinct!` differs from `unique!` in DataFrames.jl, such that `@distinct!(df, [:x,:y])` is not equal to `unique(df, [:x,:y])`.  See  **Details** for a discussion of these differences.

### Arguments

  * `d` : an AbstractDataFrame
  * `args...` :   transformations of the form `:x` designating

symbols to specify columns or `f(:x)` specifying their transformations 

### Returns

  * `::AbstractDataFrame`

Inputs to `@distinct!` can come in two formats: a `begin ... end` block, or as a series of arguments and keyword-like arguments. For example, the following are equivalent:

```julia
@distinct! df begin 
    :x .+ :y
end
```

and 

```
@distinct!(df, :x .+ :y)
```

`@distinct!` uses the syntax `@byrow` to wrap transformations in the `ByRow` function wrapper from DataFrames, apply a function row-wise, similar to broadcasting. `@distinct!` allows `@byrow` at the beginning of a block of  selections (i.e. `@byrow begin... end`). The transformation in the block  will operate by row. For example, the following two statements are equivalent.

```
@distinct! df @byrow begin 
    :x + :y
    :z + :t
end
```

and

```
@distinct! df begin 
    @byrow :x + :y
    @byrow :z + :t
end

```

### Details

The implementation of `@distinct!` differs from the `unique` function in DataFrames.jl.  When `args` are present, `@distinct!` relies upon an internal `select` call which produces  an intermediate data frame containing columns of `df` specified by `args`. The unique rows of `df` are thus determined by this intermediate data frame. This focus on `select` allows  for multiple arguments to be conveniently passed in the form of column names or transformations.

Users should be cautious when passing function arguments as vectors. E.g., `@distinct(df, $[:x,:y])` should be used instead of `@distinct(df, [:x,:y])` to avoid unexpected behaviors.

### Examples

```julia
julia> using DataFramesMeta;

julia> df = DataFrame(x = 1:10, y = 10:-1:1);

julia> @distinct!(df, :x .+ :y)
1×2 DataFrame
 Row │ x      y      
     │ Int64  Int64  
─────┼───────────────
   1 │     1      10   

julia> @distinct! df begin
            :x .+ :y
        end
1×2 DataFrame
 Row │ x      y      
     │ Int64  Int64  
─────┼───────────────
   1 │     1      10   
```
