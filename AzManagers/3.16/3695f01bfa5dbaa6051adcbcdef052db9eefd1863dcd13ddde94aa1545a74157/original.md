```
variablebundle!(;kwargs...)
```

Define variables that will be passed to a detached job.

# Example

```julia
using AzManagers
variablebundle(;x=1)
myvm = addproc("myvm")
myjob = @detachat myvm begin
    write(stdout, "my variable is $(variablebundle(:x))
")
end
wait(myjob)
read(myjob)
```
