```
mutable struct HostResolver
    ptr::Ptr{aws_host_resolver}
end
```

Default DNS host resolver.

Note on advanced use: the internal constructor on this struct has been left at its default so that you can bring your own native data if you need to. However, you are then responsible for the memory management of that data.
