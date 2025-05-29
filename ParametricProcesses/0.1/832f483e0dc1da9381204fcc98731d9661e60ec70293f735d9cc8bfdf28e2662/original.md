```julia
waitfor(pm::ProcessManager, pids::Any ...) -> ::Vector{Any}
waitfor(pm::ProcessManager) -> ::Vector{<:Any}
waitfor(f::Function, pm::ProcessManager, pids::Any ...) -> ::Vector{<:Any}
```

Stalls the main thread process to wait for all pids provided to `pids`.  Will return a `Vector{Any}` containing the completed returns for each `Worker`. Providing      no pids will `waitfor` all busy workers. Using `waitfor(f::Function, ...)` will run `f`      after `pids` are complete. –-

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
