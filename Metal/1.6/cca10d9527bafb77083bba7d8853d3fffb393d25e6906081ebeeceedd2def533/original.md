```
MemoryFlags
```

Flags to set the memory synchronization behavior of threadgroup_barrier and simdgroup_barrier.

Possible values:

```
None: Set barriers to only act as an execution barrier and not apply a memory fence.

Device: Ensure the GPU correctly orders the memory operations to device memory
        for threads in the threadgroup or simdgroup.

ThreadGroup: Ensure the GPU correctly orders the memory operations to threadgroup
        memory for threads in a threadgroup or simdgroup.

Texture: Ensure the GPU correctly orders the memory operations to texture memory for
        threads in a threadgroup or simdgroup for a texture with the read_write access qualifier.

ThreadGroup_ImgBlock: Ensure the GPU correctly orders the memory operations to threadgroup imageblock memory
        for threads in a threadgroup or simdgroup.
```
