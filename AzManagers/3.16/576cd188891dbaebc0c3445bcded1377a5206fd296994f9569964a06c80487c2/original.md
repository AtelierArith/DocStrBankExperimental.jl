```
f = machine_preempt_channel_future(pid)
```

If it exists, return a Future for a Channel allocation on the process with id `pid`, and that is used to communicate VM preemptions on `pid`.  When a worker is preempted, a Bool is put onto the channel.  Thefore, code can detect when this happens and take appropriate action before the machine corresponding to `pid` is deleted.

# Example

```julia
addproc2(template, 2; spot=true)

f = machine_preempt_channel_future(workers()[1])

remote_do(pid, f) do
    c = fetch(f)::Channel{Bool}
    while true
        if isready(c)
            @info "the VM is being preempted"
            break
        end
        sleep(1)
    end
end
```
