```
transform(df::AbstractDataFrame, args...;
          copycols::Bool=true, renamecols::Bool=true, threads::Bool=true)
transform(f::Callable, df::DataFrame;
          renamecols::Bool=true, threads::Bool=true)
transform(gd::GroupedDataFrame, args...;
          copycols::Bool=true, keepkeys::Bool=true, ungroup::Bool=true,
          renamecols::Bool=true, threads::Bool=true)
transform(f::Base.Callable, gd::GroupedDataFrame;
          copycols::Bool=true, keepkeys::Bool=true, ungroup::Bool=true,
          renamecols::Bool=true, threads::Bool=true)
```

Create a new data frame that contains columns from `df` or `gd` plus columns specified by `args` and return it. The result is guaranteed to have the same number of rows as `df`. Equivalent to `select(df, :, args...)` or `select(gd, :, args...)`.

Below detailed common rules for all transformation functions supported by DataFrames.jl are explained and compared.

All these operations are supported both for `AbstractDataFrame` (when split and combine steps are skipped) and `GroupedDataFrame`. Technically, `AbstractDataFrame` is just considered as being grouped on no columns (meaning it has a single group, or zero groups if it is empty). The only difference is that in this case the `keepkeys` and `ungroup` keyword arguments (described below) are not supported and a data frame is always returned, as there are no split and combine steps in this case.

In order to perform operations by groups you first need to create a `GroupedDataFrame` object from your data frame using the `groupby` function that takes two arguments: (1) a data frame to be grouped, and (2) a set of columns to group by.

Operations can then be applied on each group using one of the following functions:

  * `combine`: does not put restrictions on number of rows returned per group; the returned values are vertically concatenated following order of groups in `GroupedDataFrame`; it is typically used to compute summary statistics by group; for `GroupedDataFrame` if grouping columns are kept they are put as first columns in the result;
  * `select`: return a data frame with the number and order of rows exactly the same as the source data frame, including only new calculated columns; `select!` is an in-place version of `select`; for `GroupedDataFrame` if grouping columns are kept they are put as first columns in the result;
  * `transform`: return a data frame with the number and order of rows exactly the same as the source data frame, including all columns from the source and new calculated columns; `transform!` is an in-place version of `transform`; existing columns in the source data frame are put as first columns in the result;

As a special case, if a `GroupedDataFrame` that has zero groups is passed then the result of the operation is determined by performing a single call to the transformation function with a 0-row argument passed to it. The output of this operation is only used to identify the number and type of produced columns, but the result has zero rows.

All these functions take a specification of one or more functions to apply to each subset of the `DataFrame`. This specification can be of the following forms:

1. standard column selectors (integers, `Symbol`s, strings, vectors of integers, vectors of `Symbol`s, vectors of strings, `All`, `Cols`, `:`, `Between`, `Not` and regular expressions)
2. a `cols => function` pair indicating that `function` should be called with positional arguments holding columns `cols`, which can be any valid column selector; in this case target column name is automatically generated and it is assumed that `function` returns a single value or a vector; the generated name is created by concatenating source column name and `function` name by default (see examples below).
3. a `cols => function => target_cols` form additionally explicitly specifying the target column or columns, which must be a single name (as a `Symbol` or a string), a vector of names or `AsTable`. Additionally it can be a `Function` which takes a string or a vector of strings as an argument containing names of columns selected by `cols`, and returns the target columns names (all accepted types except `AsTable` are allowed).
4. a `col => target_cols` pair, which renames the column `col` to `target_cols`, which must be single name (as a `Symbol` or a string), a vector of names or `AsTable`.
5. column-independent operations `function => target_cols` or just `function` for specific `function`s where the input columns are omitted; without `target_cols` the new column has the same name as `function`, otherwise it must be single name (as a `Symbol` or a string). Supported `function`s are:

      * `nrow` to efficiently compute the number of rows in each group.
      * `proprow` to efficiently compute the proportion of rows in each group.
      * `eachindex` to return a vector holding the number of each row within each group.
      * `groupindices` to return the group number.
6. vectors or matrices containing transformations specified by the `Pair` syntax described in points 2 to 5
7. a function which will be called with a `SubDataFrame` corresponding to each group if a `GroupedDataFrame` is processed, or with the data frame itself if an `AbstractDataFrame` is processed; this form should be avoided due to its poor performance unless the number of groups is small or a very large number of columns are processed (in which case `SubDataFrame` avoids excessive compilation)

Note! If the expression of the form `x => y` is passed then except for the special convenience form `nrow => target_cols` it is always interpreted as `cols => function`. In particular the following expression `function => target_cols` is not a valid transformation specification.

Note! If `cols` or `target_cols` are one of `All`, `Cols`, `Between`, or `Not`, broadcasting using `.=>` is supported and is equivalent to broadcasting the result of `names(df, cols)` or `names(df, target_cols)`. This behaves as if broadcasting happened after replacing the selector with selected column names within the data frame scope.

All functions have two types of signatures. One of them takes a `GroupedDataFrame` as the first argument and an arbitrary number of transformations described above as following arguments. The second type of signature is when a `Function` or a `Type` is passed as the first argument and a `GroupedDataFrame` as the second argument (similar to `map`).

As a special rule, with the `cols => function` and `cols => function => target_cols` syntaxes, if `cols` is wrapped in an `AsTable` object then a `NamedTuple` containing columns selected by `cols` is passed to `function`. The documentation of [`DataFrames.table_transformation`](@ref) provides more information about this functionality, in particular covering performance considerations.

What is allowed for `function` to return is determined by the `target_cols` value:

1. If both `cols` and `target_cols` are omitted (so only a `function` is passed), then returning a data frame, a matrix, a `NamedTuple`, a `Tables.AbstractRow` or a `DataFrameRow` will produce multiple columns in the result. Returning any other value produces a single column.
2. If `target_cols` is a `Symbol` or a string then the function is assumed to return a single column. In this case returning a data frame, a matrix, a `NamedTuple`, a `Tables.AbstractRow`, or a `DataFrameRow` raises an error.
3. If `target_cols` is a vector of `Symbol`s or strings or `AsTable` it is assumed that `function` returns multiple columns. If `function` returns one of `AbstractDataFrame`, `NamedTuple`, `DataFrameRow`, `Tables.AbstractRow`, `AbstractMatrix` then rules described in point 1 above apply. If `function` returns an `AbstractVector` then each element of this vector must support the `keys` function, which must return a collection of `Symbol`s, strings or integers; the return value of `keys` must be identical for all elements. Then as many columns are created as there are elements in the return value of the `keys` function. If `target_cols` is `AsTable` then their names are set to be equal to the key names except if `keys` returns integers, in which case they are prefixed by `x` (so the column names are e.g. `x1`, `x2`, ...). If `target_cols` is a vector of `Symbol`s or strings then column names produced using the rules above are ignored and replaced by `target_cols` (the number of columns must be the same as the length of `target_cols` in this case). If `fun` returns a value of any other type then it is assumed that it is a table conforming to the Tables.jl API and the `Tables.columntable` function is called on it to get the resulting columns and their names. The names are retained when `target_cols` is `AsTable` and are replaced if `target_cols` is a vector of `Symbol`s or strings.

In all of these cases, `function` can return either a single row or multiple rows. As a particular rule, values wrapped in a `Ref` or a `0`-dimensional `AbstractArray` are unwrapped and then treated as a single row.

`select`/`select!` and `transform`/`transform!` always return a data frame with the same number and order of rows as the source (even if `GroupedDataFrame` had its groups reordered), except when selection results in zero columns in the resulting data frame (in which case the result has zero rows).

For `combine`, rows in the returned object appear in the order of groups in the `GroupedDataFrame`. The functions can return an arbitrary number of rows for each group, but the kind of returned object and the number and names of columns must be the same for all groups, except when a `DataFrame()` or `NamedTuple()` is returned, in which case a given group is skipped.

It is allowed to mix single values and vectors if multiple transformations are requested. In this case single value will be repeated to match the length of columns specified by returned vectors.

To apply `function` to each row instead of whole columns, it can be wrapped in a `ByRow` struct. `cols` can be any column indexing syntax, in which case `function` will be passed one argument for each of the columns specified by `cols` or a `NamedTuple` of them if specified columns are wrapped in `AsTable`. If `ByRow` is used it is allowed for `cols` to select an empty set of columns, in which case `function` is called for each row without any arguments and an empty `NamedTuple` is passed if empty set of columns is wrapped in `AsTable`.

If a collection of column names is passed then requesting duplicate column names in target data frame are accepted (e.g. `select!(df, [:a], :, r"a")` is allowed) and only the first occurrence is used. In particular a syntax to move column `:col` to the first position in the data frame is `select!(df, :col, :)`. On the contrary, output column names of renaming, transformation and single column selection operations must be unique, so e.g. `select!(df, :a, :a => :a)` or `select!(df, :a, :a => ByRow(sin) => :a)` are not allowed.

In general columns returned by transformations are stored in the target data frame without copying. An exception to this rule is when columns from the source data frame are reused in the target data frame. This can happen via expressions like: `:x1`, `[:x1, :x2]`, `:x1 => :x2`, `:x1 => identity => :x2`, or `:x1 => (x -> @view x[inds])` (note that in the last case the source column is reused indirectly via a view). In such cases the behavior depends on the value of the `copycols` keyword argument:

  * if `copycols=true` then results of such transformations always perform a copy of the source column or its view;
  * if `copycols=false` then copies are only performed to avoid storing the same column several times in the target data frame; more precisely, no copy is made the first time a column is used, but each subsequent reuse of a source column (when compared using `===`, which excludes views of source columns) performs a copy;

Note that performing `transform!` or `select!` assumes that `copycols=false`.

If `df` is a `SubDataFrame` and `copycols=true` then a `DataFrame` is returned and the same copying rules apply as for a `DataFrame` input: this means in particular that selected columns will be copied. If `copycols=false`, a `SubDataFrame` is returned without copying columns and in this case transforming or renaming columns is not allowed.

If a `GroupedDataFrame` is passed and `threads=true` (the default), a separate task is spawned for each specified transformation; each transformation then spawns as many tasks as Julia threads, and splits processing of groups across them (however, currently transformations with optimized implementations like `sum` and transformations that return multiple rows use a single task for all groups). This allows for parallel operation when Julia was started with more than one thread. Passed transformation functions must therefore not modify global variables (i.e. they must be pure), use locks to control parallel accesses, or `threads=false` must be passed to disable multithreading. In the future, parallelism may be extended to other cases, so this requirement also holds for `DataFrame` inputs.

In order to improve the performance of the operations some transformations invoke optimized implementation, see [`DataFrames.table_transformation`](@ref) for details.

# Keyword arguments

  * `copycols::Bool=true` : whether columns of the source data frame should be copied if no transformation is applied to them.
  * `renamecols::Bool=true` : whether in the `cols => function` form automatically generated column names should include the name of transformation functions or not.
  * `keepkeys::Bool=true` : whether grouping columns of `gd` should be kept in the returned data frame.
  * `ungroup::Bool=true` : whether the return value of the operation on `gd` should be a data frame or a `GroupedDataFrame`.
  * `threads::Bool=true` : whether transformations may be run in separate tasks which can execute in parallel (possibly being applied to multiple rows or groups at the same time). Whether or not tasks are actually spawned and their number are determined automatically. Set to `false` if some transformations require serial execution or are not thread-safe.

Note that when the first argument is a `GroupedDataFrame`, `keepkeys=false` is needed to be able to return a different value for the grouping column:

Metadata: this function propagates table-level `:note`-style metadata. Column-level `:note`-style metadata is propagated if: a) a single column is transformed to a single column and the name of the column   does not change (this includes all column selection operations), or b) a single column is transformed with `identity` or `copy` to a single column    even if column name is changed (this includes column renaming).    As a special case for `GroupedDataFrame` if the output has the same name    as a grouping column and `keepkeys=true`, metadata is taken from    original grouping column.

# Examples

```jldoctest
julia> gdf = groupby(DataFrame(x=1:2), :x)
GroupedDataFrame with 2 groups based on key: x
First Group (1 row): x = 1
 Row │ x
     │ Int64
─────┼───────
   1 │     1
⋮
Last Group (1 row): x = 2
 Row │ x
     │ Int64
─────┼───────
   1 │     2

julia> transform(gdf, x -> (x=10,), keepkeys=false)
2×1 DataFrame
 Row │ x
     │ Int64
─────┼───────
   1 │    10
   2 │    10

julia> transform(gdf, x -> (x=10,), keepkeys=true)
ERROR: ArgumentError: column :x in returned data frame is not equal to grouping key :x
```

See [`select`](@ref) for more examples.
