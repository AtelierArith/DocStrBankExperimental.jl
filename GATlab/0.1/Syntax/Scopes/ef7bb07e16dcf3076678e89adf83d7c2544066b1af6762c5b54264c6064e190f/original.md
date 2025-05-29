`ident` creates an `Ident` from a context and some partial data supplied as keywords.

Keywords arguments:

  * `tag::Union{ScopeTag, Nothing}`. The tag of the scope that the `Ident` is in.
  * `name::Union{Symbol, Nothing}`. The name of the identifier.
  * `lid::Union{LID, Nothing}`. The lid of the identifier within its scope.
  * `level::Union{Int, Nothing}`. The level of the scope within the context.
  * `strict::Bool`. If `strict` is true, throw an error if not found, else return nothing.
