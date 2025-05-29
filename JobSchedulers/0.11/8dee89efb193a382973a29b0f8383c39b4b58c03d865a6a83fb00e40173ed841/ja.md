```
Job(command::Base.AbstractCmd; stdout=nothing, stderr=nothing, append::Bool=false, kwargs...)
Job(f::Function; kwargs...)
Job(task::Task; kwargs...)
```

# 引数

  * `command::Base.AbstractCmd`: 実行するコマンド。
  * `f::Function`: 引数なしで実行する関数、例えば `f()`。
  * `task::Task`: 実行するタスク。例: `@task(1+1)`。

# 一般的なキーワード引数 (kwargs...)

  * `name::String = ""`: ジョブ名。
  * `user::String = ""`: ジョブが属するユーザー。
  * `ncpu::Real = 1.0`: このジョブが使用するCPUの数（`Float64`を使用可能、例: `1.5`は150%のCPUを使用）。
  * `mem::Integer = 0`: このジョブが使用するメモリの数（TB、GB、MB、KB、B=1をサポート）。
  * `schedule_time::Union{DateTime,Period} = DateTime(0)`: 実行予定時間。
  * `dependency`: 指定されたジョブが指定された状態（QUEUING, RUNNING, DONE, FAILED, CANCELLED, PAST）に達するまでジョブを遅延させる。PASTはDONE、FAILED、CANCELLEDのスーパーセットであり、将来的にジョブが実行されないことを意味する。例: `DONE => job`, `[DONE => job1; PAST => job2]`。

!!! info "依存関係"
    デフォルトの状態はDONEであるため、`DONE => job`は`job`に簡略化できます。古いバージョンとの互換性を保つために、ジョブID（Int）を使用することもできます: `[DONE => job.id]`。


  * `wall_time::Period = Year(1)`: 実行時間制限。ジョブはこの期間が経過した後に終了します。
  * `priority::Int = 20`: 数値が低いほど優先度が高い。
  * `cron::Cron = Cron(:none)`: 特定の日付と時間に繰り返し実行されるジョブ。詳細は[`Cron`](@ref)を参照。
  * `until::Union{DateTime,Period} = DateTime(9999,1,1)`: ジョブの繰り返しを`until`の日付と時間で停止します。

# 実験的キーワード引数 - 出力リダイレクション:

  * `stdout=nothing`: stdoutをファイルにリダイレクト。
  * `stderr=nothing`: stderrをファイルにリダイレクト。
  * `append::Bool=false`: stdoutまたはstderrを追加するかどうか。

!!! note
    Juliaでのリダイレクションはスレッドセーフではないため、異なる`Tasks`でプログラムを同時に実行している場合、予期しないリダイレクションが発生する可能性があります（マルチスレッド）。


他にも[`submit!`](@ref)、[`@submit`](@ref)、[`Cron`](@ref)を参照してください。
