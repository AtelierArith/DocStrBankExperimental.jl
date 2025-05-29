```
supervisor(
    id, processes;
    intensity=DEFAULT_INTENSITY,
    period=DEFAULT_PERIOD,
    strategy=:one_for_one,
    terminateif=:empty)::SupervisorSpec
```

1つ以上の `processes` のスーパーバイザーを宣言します。

`processes` は `Process` または `Process` の配列である可能性があります。

```jldoctest
julia> using Visor

julia> mytask(pd) = ();

julia> supervisor("mysupervisor", process(mytask))
mysupervisor
```

```jldoctest julia> using Visor

julia> tsk1(pd) = ();

julia> tsk2(pd) = ();

julia> supervisor("mysupervisor", [process(tsk1), process(tsk2)]) mysupervisor

詳細については [Supervisor](@ref) ドキュメントを参照してください。
```
