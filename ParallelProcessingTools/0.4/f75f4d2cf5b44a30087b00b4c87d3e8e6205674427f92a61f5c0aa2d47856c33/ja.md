```
HTCondorRun(;
    n::Int = 1
    condor_flags::Cmd = _default_condor_flags()
    condor_settings::Dict{String,String} = Dict{String,String}()
    julia_flags::Cmd = _default_julia_flags()
    julia_depot::Vector{String} = DEPOT_PATH
    jobfile_dir = homedir()
    env::Dict{String,String} = Dict{String,String}()
    redirect_output::Bool = true
)
```

HTCondor `condor_submit`を介してワーカープロセスを追加するモード。

Condor提出スクリプトと制御`.sh`ファイルは`jobfile_dir`に保存されます。

例:

```julia-repl
julia> runmode = HTCondorRun(n = 10; condor_settings=Dict("universe" => "vanilla", "+queue" => "short", "request_memory" => "4GB"))
task = runworkers(runmode)

julia> runworkers(runmode)
[ Info: HTCondorジョブを提出中: `condor_submit /home/jiling/jl_rAHyFadwHa.sub`
ジョブを提出中..........
10ジョブがクラスター3198291に提出されました。
[ Info: HTCondorジョブが提出されました: `condor_submit /home/jiling/jl_rAHyFadwHa.sub`
(nothing, 10)

julia> sleep(10)

julia> nworkers()
10
```

ワーカーは手動でも開始できます。[`worker_start_command(runmode)`](@ref)を使用して`condor_submit`開始コマンドを取得し、別のプロセスから実行することができます。
