```
OnLocalhost(;
    n::Integer = 1
    env::Dict{String,String} = Dict{String,String}()
) isa DynamicAddProcsMode
```

現在のホストで `n` ワーカープロセスを実行するモードです。

例:

```julia
runmode = OnLocalhost(n = 4)
task, n = runworkers(runmode)

Threads.@async begin
    wait(task)
    @info "SLURM ワーカーが終了しました。"
end

@wait_while nprocs()-1 < n)
```

ワーカーは手動でも起動できます。 [`worker_start_command(runmode)`](@ref) を使用してシステム（シェル）コマンドを取得し、別のプロセスから実行することができます。
