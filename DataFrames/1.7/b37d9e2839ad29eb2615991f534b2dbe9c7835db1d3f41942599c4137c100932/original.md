```
flatten(df::AbstractDataFrame, cols; scalar::Type=Union{})
```

When columns `cols` of data frame `df` have iterable elements that define `length` (for example a `Vector` of `Vector`s), return a `DataFrame` where each element of each `col` in `cols` is flattened, meaning the column corresponding to `col` becomes a longer vector where the original entries are concatenated. Elements of row `i` of `df` in columns other than `cols` will be repeated according to the length of `df[i, col]`. These lengths must therefore be the same for each `col` in `cols`, or else an error is raised. Note that these elements are not copied, and thus if they are mutable changing them in the returned `DataFrame` will affect `df`.

`cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers).

If `scalar` is passed then values that have this type in flattened columns are treated as scalars and broadcasted as many times as is needed to match lengths of values stored in other columns. If all values in a row are scalars, a single row is produced.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> df1 = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7, 8]])
2×3 DataFrame
 Row │ a      b       c
     │ Int64  Array…  Array…
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7, 8]

julia> flatten(df1, :b)
4×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Array…
─────┼──────────────────────
   1 │     1      1  [5, 6]
   2 │     1      2  [5, 6]
   3 │     2      3  [7, 8]
   4 │     2      4  [7, 8]

julia> flatten(df1, [:b, :c])
4×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      1      5
   2 │     1      2      6
   3 │     2      3      7
   4 │     2      4      8

julia> df2 = DataFrame(a=[1, 2], b=[("p", "q"), ("r", "s")])
2×2 DataFrame
 Row │ a      b
     │ Int64  Tuple…
─────┼───────────────────
   1 │     1  ("p", "q")
   2 │     2  ("r", "s")

julia> flatten(df2, :b)
4×2 DataFrame
 Row │ a      b
     │ Int64  String
─────┼───────────────
   1 │     1  p
   2 │     1  q
   3 │     2  r
   4 │     2  s

julia> df3 = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7]])
2×3 DataFrame
 Row │ a      b       c
     │ Int64  Array…  Array…
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7]

julia> flatten(df3, [:b, :c])
ERROR: ArgumentError: Lengths of iterables stored in columns :b and :c are not the same in row 2

julia> df4 = DataFrame(a=[1, 2, 3],
                       b=[[1, 2], missing, missing],
                       c=[[5, 6], missing, [7, 8]])
3×3 DataFrame
 Row │ a      b        c
     │ Int64  Array…?  Array…?
─────┼─────────────────────────
   1 │     1  [1, 2]   [5, 6]
   2 │     2  missing  missing
   3 │     3  missing  [7, 8]

julia> flatten(df4, [:b, :c], scalar=Missing)
5×3 DataFrame
 Row │ a      b        c
     │ Int64  Int64?   Int64?
─────┼─────────────────────────
   1 │     1        1        5
   2 │     1        2        6
   3 │     2  missing  missing
   4 │     3  missing        7
   5 │     3  missing        8
```
