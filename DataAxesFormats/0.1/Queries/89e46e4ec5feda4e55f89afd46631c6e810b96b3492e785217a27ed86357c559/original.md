Specify a column for [`get_frame`](@ref) for some axis. The most generic form is a pair `"column_name" => query`. Two shorthands apply: the pair `"column_name" => "="` is a shorthand for the pair `"column_name" => ": column_name"`, and so is the shorthand `"column_name"` (simple string).

We also allow specifying tuples instead of pairs to make it easy to invoke the API from other languages such as Python which do not have the concept of a `Pair`.

The query is combined with the axis query as follows (using [`full_vector_query`](@ref):

  * If the query contains [`GroupBy`](@ref), then the query must repeat any mask specified for the axis query. That is, if the axis query is `metacell & type = B`, then the column query must be `/ cell & metacell => type = B @ metacell : age %> Mean`. Sorry for the inconvenience. TODO: Automatically inject the mask into [`GroupBy`](@ref) column queries.
  * Otherwise, if the query starts with a (single) axis, then it should only contain a reduction; the axis query is automatically injected following it. That is, if the axis query is `gene & is_marker`, then the full query for the column query `/ metacell : fraction %> Mean` will be `/ metacell / gene : fraction %> Mean` (the mean gene expression in all metacells). We can't just concatenate the axis query and the columns query here, is because Julia, in its infinite wisdom, uses column-major matrices, like R and matlab; so reduction eliminates the rows instead of the columns of the matrix.
  * Otherwise (the typical case), we simply concatenate the axis query and the column query. That is, of the axis query is `cell & batch = B1` and the column query is `: age`, then the full query will be `cell & batch = B1 : age`. This is the simplest and most common case.

In all cases the (full) query must return a value for each entry of the axis.
