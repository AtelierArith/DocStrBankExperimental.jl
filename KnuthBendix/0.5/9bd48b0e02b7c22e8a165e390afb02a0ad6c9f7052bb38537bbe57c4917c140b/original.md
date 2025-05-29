```
isconfluent(rws::RewritingSystem)
```

Check whether the rewriting system is confluent.

!!! note
    Since [`check_confluence`](@ref) is relatively cheap only for **reduced** rewriting systems `isconfluent` will not try to reduce the system on its own and will return `false`. For definitive answer one should [`reduce!`](@ref) the rewrting system before calling `isconfluent`.

