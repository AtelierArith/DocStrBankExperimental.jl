coerce!(X, ...)

[`ScientificTypes.coerce`](@ref) と同じですが、`X` がインプレース修正をサポートしている場合（例：DataFrames）に限り、インプレースで修正を行います。それ以外の場合はエラーが発生します。引数は `coerce` と同じです。
