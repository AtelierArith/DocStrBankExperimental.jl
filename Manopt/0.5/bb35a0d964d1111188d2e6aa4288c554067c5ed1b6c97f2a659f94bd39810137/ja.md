```
get_reason(s::AbstractManoptSolverState)
```

[`AbstractManoptSolverState`](@ref)内の[`StoppingCriterion`](@ref)に格納されている現在の理由を返します。この理由は、基準が一度も満たされていない場合は空（`""`）です。
