```
SlurmRun(;
    slurm_flags::Cmd = {defaults}
    julia_flags::Cmd = {defaults}
    dir = pwd()
    env::Dict{String,String} = Dict{String,String}()
    redirect_output::Bool = true
)
```

SLURM `srun`を介してワーカープロセスを追加するモード。

`srun`およびJuliaワーカー`julia`コマンドラインフラグは、SLURM環境変数（例：`salloc`またはバッチジョブ内）および`slurm_flags`と`julia_flags`から推測されます。

ワーカーは、現在のディレクトリが`dir`に設定されて開始されます。

例：

```julia
runmode = SlurmRun(slurm_flags = `--ntasks=4 --cpus-per-task=8 --mem-per-cpu=8G`)
task = runworkers(runmode)

Threads.@async begin
    wait(task)
    @info "SLURM workers have terminated."
end

@wait_while nprocs()-1 < n
```

ワーカーは手動でも開始できます。[`worker_start_command(runmode)`](@ref)を使用して`srun`開始コマンドを取得し、別のプロセスから実行することができます。
