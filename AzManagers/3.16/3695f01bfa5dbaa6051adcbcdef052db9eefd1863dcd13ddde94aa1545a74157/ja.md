```
variablebundle!(;kwargs...)
```

切り離されたジョブに渡される変数を定義します。

# 例

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
