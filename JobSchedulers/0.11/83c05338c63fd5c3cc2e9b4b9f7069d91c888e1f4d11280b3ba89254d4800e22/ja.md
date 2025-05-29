```
set_scheduler_max_cpu(ncpu::Int = default_ncpu())
set_scheduler_max_cpu(percent::Float64)
```

スケジューラが使用できる最大CPU（スレッド）を設定します。デフォルトのスレッドプールで複数のスレッドを使用してJuliaを起動する場合、最大CPUはデフォルトのスレッドプール内のtidsの数で、1ではありません。

# 例

```
set_scheduler_max_cpu()     # 使用可能なすべてのCPUを使用
set_scheduler_max_cpu(4)    # 4つのCPUを使用
set_scheduler_max_cpu(0.5)  # CPUの50%を使用
```
