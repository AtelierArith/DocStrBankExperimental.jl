```
@astable(args...)
```

Return a `NamedTuple` from a single transformation inside the DataFramesMeta.jl macros, `@select`, `@transform`, and their mutating and row-wise equivalents.

`@astable` acts on a single block. It works through all top-level expressions and collects all such expressions of the form `:y = ...` or `$y = ...`, i.e. assignments to a `Symbol` or an escaped column identifier, which is a syntax error outside of DataFramesMeta.jl macros. At the end of the expression, all assignments are collected into a `NamedTuple` to be used with the `AsTable` destination in the DataFrames.jl transformation mini-language.

Concretely, the expressions

```
df = DataFrame(a = 1)

@rtransform df @astable begin
    :x = 1
    y = 50
    :z = :x + y + :a
end
```

become the pair

```
function f(a)
    x_t = 1
    y = 50
    z_t = x_t + y + a

    (; x = x_t, z = z_t)
end

transform(df, [:a] => ByRow(f) => AsTable)
```

`@astable` has two major advantages at the cost of increasing complexity. First, `@astable` makes it easy to create multiple columns from a single transformation, which share a scope. For example, `@astable` allows for the following (where `:x` and `:x_2` exist in the data frame already).

```
@transform df @astable begin
    m = mean(:x)
    :x_demeaned = :x .- m
    :x2_demeaned = :x2 .- m
end
```

The creation of `:x_demeaned` and `:x2_demeaned` both share the variable `m`, which does not need to be calculated twice.

Second, `@astable` is useful when performing intermediate calculations and storing their results in new columns. For example, the following fails.

```
@rtransform df begin
    :new_col_1 = :x + :y
    :new_col_2 = :new_col_1 + :z
end
```

This because DataFrames.jl does not guarantee sequential evaluation of transformations. `@astable` solves this problem

@rtransform df @astable begin     :new*col*1 = :x + :y     :new*col*2 = :new*col*1 + :z end

Column assignment in `@astable` follows similar rules as column assignment in other DataFramesMeta.jl macros. The left- -hand-side of a column assignment can be either a `Symbol` or any expression which evaluates to a `Symbol` or `AbstractString`. For example `:y = ...`, and `$y = ...` are both valid ways of assigning a new column. However unlike other DataFramesMeta.jl macros, multi-column assignments via `AsTable` are disallowed. The following will fail.

```
@transform df @astable begin
    DataFrames.AsTable = :x
end
```

References to existing columns also follow the same rules as other DataFramesMeta.jl macros.

### Examples

```
julia> df = DataFrame(a = [1, 2, 3], b = [4, 5, 6]);

julia> d = @rtransform df @astable begin
           :x = 1
           y = 5
           :z = :x + y
       end
3×4 DataFrame
 Row │ a      b      x      z
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      4      1      6
   2 │     2      5      1      6
   3 │     3      6      1      6

julia> df = DataFrame(a = [1, 1, 2, 2], b = [5, 6, 70, 80]);

julia> @by df :a @astable begin
            ex = extrema(:b)
            :min_b = first(ex)
            :max_b = last(ex)
       end
2×3 DataFrame
 Row │ a      min_b  max_b
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      5      6
   2 │     2     70     80

julia> new_col = "New Column";

julia> @rtransform df @astable begin
           f_a = first(:a)
           $new_col = :a + :b + f_a
           :y = :a * :b
       end
4×4 DataFrame
 Row │ a      b      New Column  y
     │ Int64  Int64  Int64       Int64
─────┼─────────────────────────────────
   1 │     1      5           7      5
   2 │     1      6           8      6
   3 │     2     70          74    140
   4 │     2     80          84    160
```
