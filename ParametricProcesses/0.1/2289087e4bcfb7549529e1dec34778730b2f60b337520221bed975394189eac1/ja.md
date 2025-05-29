```julia
ProcessJob <: AbstractJob
```

  * f**::Function**
  * args
  * kwargs

`ProcessJob`はデフォルトの`ParametericProcess`ジョブタイプです。このコンストラクタは`new_job`としても定義されています。`new_job`（またはこのコンストラクタ）に`Function`とその`Function`の引数を提供し、その後`assign!`または`distribute!`を使用してプロセスマネージャにジョブを提供します。

  * 参照: `Worker`, `processes`, `ProcessManager`, `assign!`

```julia
- ProcessJob(f::Function, args ...; keyargs ...)
```

---

```example
# note this is `julia --threads >2`
newprocs = processes(3)
io = IOBuffer()
new_job = (io) do o
    write(o, "hello world!)
end

assign!(newprocs, 2, [new_job for e in 1:50] ...)
```
