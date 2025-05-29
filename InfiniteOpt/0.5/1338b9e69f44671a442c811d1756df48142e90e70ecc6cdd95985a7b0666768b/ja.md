```
set_all_derivative_methods(model::InfiniteModel, 
                           method::AbstractDerivativeMethod)::Nothing
```

現在モデルに追加されているすべての導関数に対して、希望する評価方法 `method` を設定します。これは無限パラメータに関して行われることに注意してください。生成的な方法が指定され、モデルに依存パラメータが含まれている場合はエラーが発生します。

**例**

```julia-repl
julia> set_all_derivative_methods(model, OrthogonalCollocation(2))

```
