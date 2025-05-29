```
no_failure!(body::AbstractBody, set_name::Symbol)
no_failure!(body::AbstractBody)
```

`set_name`の点集合のすべての点に対して失敗を禁止します。`set_name`が指定されていない場合、`body`全体に対して失敗が禁止されます。

# 引数

  * `body::AbstractBody`: 失敗が禁止される[`Body`](@ref)。
  * `set_name::Symbol`: このボディの点集合の名前。

!!! danger " `material!` と `no_failure!` で失敗の許可を上書きする"
    関数 `material!` は提供された入力パラメータに基づいて失敗の許可を設定するため、その後に使用されると、以前に設定された失敗禁止が上書きされる可能性があります！


# 例外

  * `set_name`を持つ集合がボディに含まれていない場合、エラーが発生します。

# 例

```julia-repl
julia> no_failure!(body)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  1000 points with failure prohibited
```
