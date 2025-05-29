```
lint(obj::T)
```

Call all of the relevant linter functions on `obj`. More specifically, the method table is searched for `lint(obj::T, ::Val{:linter_id})` methods (where `:linter_id` is a stand-in for the actual IDs used), and each specific lint function is invoked and the results combined.

!!! note
    Each specific linter function should return a vector of relevant `LintItem`s, i.e.

    ```julia
    lint(obj::T, ::Val{:linter_id}) -> Union{Vector{LintItem{T}}, LintItem{T}, Nothing}
    ```

    See the documentation on `LintItem` for more information on how it should be constructed.

