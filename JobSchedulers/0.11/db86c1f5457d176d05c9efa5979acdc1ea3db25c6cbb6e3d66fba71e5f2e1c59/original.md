```
set_scheduler_max_mem(mem::Integer = default_mem())
set_scheduler_max_mem(percent::AbstractFloat)
```

Set the maximum RAM the scheduler can use.

# Example

```
set_scheduler_max_mem()             # use 80% of total memory

set_scheduler_max_mem(4GB)          # use 4GB memory
set_scheduler_max_mem(4096MB)
set_scheduler_max_mem(4194304KB)
set_scheduler_max_mem(4294967296B)

set_scheduler_max_mem(0.5)          # use 50% of total memory
```
