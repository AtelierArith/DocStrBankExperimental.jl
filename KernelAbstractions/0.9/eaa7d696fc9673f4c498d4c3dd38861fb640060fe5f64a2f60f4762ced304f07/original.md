```
@synchronize()
```

After a `@synchronize` statement all read and writes to global and local memory from each thread in the workgroup are visible in from all other threads in the workgroup.

!!! note
    `@synchronize()` must be encountered by all workitems of a work-group executing the kernel or by none at all.

