```
revise(; throw=false)
```

`eval` 変更をリビジョンキューに適用します。 [`Revise.revision_queue`](@ref)を参照してください。 `throw` が `true` の場合、リビジョンまたはコールバック中に発生したエラーをスローします。それ以外の場合、これらはログに記録されるだけです。
