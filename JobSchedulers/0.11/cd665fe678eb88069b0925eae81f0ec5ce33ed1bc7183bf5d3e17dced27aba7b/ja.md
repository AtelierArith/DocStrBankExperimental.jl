```julia
queue(; all::Bool = false)    -> Vector{Job}
queue(state::Symbol )         -> Vector{Job}
queue(needle)                 -> Vector{Job}
queue(state::Symbol , needle) -> Vector{Job}
queue(needle, state::Symbol ) -> Vector{Job}
queue(id::Integer)            -> Job
```

  * `all::Bool`: true の場合、すべてのジョブを取得します。false の場合、実行中およびキューにあるジョブのみを取得します。
  * `state::Symbol`: 特定の状態のジョブを取得します。状態には `:all`、`QUEUING`、`RUNNING`、`DONE`、`FAILED`、`CANCELLED`、`PAST` が含まれます。

    > `PAST` は `DONE`、`FAILED`、`CANCELLED` のスーパーセットです。
  * `needle::Union{AbstractString,AbstractPattern,AbstractChar}`: 名前またはユーザーに `needle` を含むジョブを取得します。
  * `id::Integer`: 特定の `id` を持つジョブを取得します。
