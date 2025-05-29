```
Query(
    query::QueryString,
    operand_only::Maybe{Type{QueryOperation}} = nothing,
) <: QueryOperation
```

A query is a description of a (sub-)process for extracting some data from a [`DafReader`](@ref). A full query is a sequence of [`QueryOperation`](@ref), that when applied one at a time on some [`DafReader`](@ref), result in a scalar, vector or matrix result.

To apply a query, invoke [`get_query`](@ref) to apply a query to some [`DafReader`](@ref) data (you can also use the shorthand $daf[query]$ instead of $get_query(daf, query)$). By default, query operations will cache their results in memory as [`QueryData`](@ref CacheGroup), to speed up repeated queries. This may lock up large amounts of memory; you can [`empty_cache!`](@ref) to release it.

Queries can be constructed in two ways. In code, a query can be built by chaining query operations (e.g., the expression `Axis("gene") |> Lookup("is_marker")` looks up the `is_marker` vector property of the `gene` axis).

Alternatively, a query can be parsed from a string, which needs to be parsed into a [`Query`](@ref) object (e.g., the above can be written as `Query("/gene:is_marker")`). See the [`QUERY_OPERATORS`](@ref) for a table of supported operators. Spaces (and comments) around the operators are optional; see [`tokenize`](@ref) for details. You can also convert a [`Query`](@ref) to a `string` (or `print` it, etc.) to see its representation. This is used for `error` messages and as a key when caching query results.

Since query strings use `\` as an escape character, it is easier to use `raw` string literals for queries (e.g., `Query(raw"cell = ATCG\:B1 : age")` vs. `Query("cell = ATCG\\:B1 : age")`). To make this even easier we provide the [`q`](@ref @q_str) macro (e.g., `q"cell = ATCG\:B1 : batch"`) which works similarly to Julia's standard `r` macro for literal `Regex` strings.

If the provided query string contains only an operand, and `operand_only` is specified, it is used as the operator (i.e., `Query("metacell")` is an error, but `Query("metacell", Axis)` is the same as `Axis("metacell")`). This is useful when providing suffix queries (e.g., for [`get_frame`](@ref)).

Being able to represent queries as strings allows for reading them from configuration files and letting the user input them in an application UI (e.g., allowing the user to specify the X, Y and/or colors of a scatter plot using queries). At the same time, being able to incrementally build queries using code allows for convenient reuse (e.g., reusing axis sub-queries in `Daf` views), without having to go through the string representation.

`Daf` provides a comprehensive set of [`QueryOperation`](@ref)s that can be used to construct queries. The [`QUERY_OPERATORS`](@ref) listed below provide the basic functionality (e.g., specifying an [`Axis`](@ref) or a property [`Lookup`](@ref)). In addition, `Daf` provides computation operations ([`EltwiseOperation`](@ref) and [`ReductionOperation`](@ref)), allowing for additional operations to be provided by external packages.

Obviously not all possible combinations of operations make sense (e.g., `Lookup("is_marker") |> Axis("cell")` will not work). For the full list of valid combinations, see [`NAMES_QUERY`](@ref), [`SCALAR_QUERY`](@ref), [`VECTOR_QUERY`](@ref) and [`MATRIX_QUERY`](@ref) below.

!!! note
    This has started as a very simple query language (which it still is, for the simple cases) but became complex to allow for useful but complicated scenarios. In particular, the approach here of using a concatenative language (similar to `ggplot`) makes simple things simpler, but becames somewhat unnatural and restrictive for some of the more advanced operations. However, using an RPN or a LISP notation to better support such cases would have ended up with a much less nice syntax for the simple cases.

    Hopefully we have covered sufficient ground so that we won't need to add further operations. Also, In most cases, you can write code that accesses the vectors/matrix data and performs whatever computation you want instead of writing a complex query; however, this isn't an option when defining views or adapters, which rely on the query mechanism for specifying the data.

