```julia
waitfor(pm::ProcessManager, pids::Any ...) -> ::Vector{Any}
waitfor(pm::ProcessManager) -> ::Vector{<:Any}
waitfor(f::Function, pm::ProcessManager, pids::Any ...) -> ::Vector{<:Any}
```

メインスレッドプロセスを停止して、`pids`に提供されたすべてのpidsを待機します。完了した各`Worker`の戻り値を含む`Vector{Any}`を返します。pidsを提供しない場合、`waitfor`はすべてのビジーなワーカーを待機します。`waitfor(f::Function, ...)`を使用すると、`pids`が完了した後に`f`が実行されます。 –-

```example
pm = processes(4)

jb = new_job() do 
    sleep(10)
    @info "hello world!"
    return 55
end

assign!(pm, 2, jb)

ret = waitfor(pm, 2); println("worker 2 completed, it returned: ", ret[1])

# From worker 2:	[ Info: hello world!
# worker 2 completed, it returned: 55
```
