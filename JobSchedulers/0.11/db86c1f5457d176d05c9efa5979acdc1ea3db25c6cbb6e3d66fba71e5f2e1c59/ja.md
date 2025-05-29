```
set_scheduler_max_mem(mem::Integer = default_mem())
set_scheduler_max_mem(percent::AbstractFloat)
```

スケジューラが使用できる最大RAMを設定します。

# 例

```
set_scheduler_max_mem()             # 総メモリの80%を使用

set_scheduler_max_mem(4GB)          # 4GBのメモリを使用
set_scheduler_max_mem(4096MB)
set_scheduler_max_mem(4194304KB)
set_scheduler_max_mem(4294967296B)

set_scheduler_max_mem(0.5)          # 総メモリの50%を使用
```
