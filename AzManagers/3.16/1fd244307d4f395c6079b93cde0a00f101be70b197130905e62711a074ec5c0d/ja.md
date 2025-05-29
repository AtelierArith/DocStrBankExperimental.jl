```
@detachat myvm begin ... end
```

Azure VMでコードを実行します。

# 例

```
using AzManagers
myvm = addproc("myvm")
job = @detachat myvm begin
    @info "私はデタッチモードで実行しています"
end
read(job)
wait(job)
rmproc(myvm)
```
