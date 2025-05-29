```
mutable struct SlabBuffer{SlabSize}
```

A slab-based bump allocator which can dynamically grow to hold an arbitrary amount of memory. Small allocations live within a specific slab of memory, and if that slab fills up, a new slab is allocated and future allocations happen on that slab. Small allocations are stored in slabs of size `SlabSize` bytes, and the list of live slabs are tracked in the `slabs` field. Allocations which are too large to fit into one slab are stored and tracked in the `custom_slabs` field.

The default slab size is 1048576 bytes.

`SlabBuffer`s are nearly as fast as stack allocation (typically up to within a couple of nanoseconds) for typical use. One potential performance pitfall is if that `SlabBuffer`'s current position is at the end of a slab, then the next allocation will be slow because it requires a new slab to be created. This means that if you do something like

```
buf = SlabBuffer{N}()
@no_escape buf begin
    @alloc(Int8, N÷2 - 1) # Take up just under half the first slab
    @alloc(Int8, N÷2 - 1) # Take up another half of the first slab
    # Now buf should be practically out of room. 
    for i in 1:1000
        @no_escape buf begin
            y = @alloc(Int8, 10) # This will allocate a new slab because there's no room
            f(y)
        end # At the end of this block, we delete the new slab because it's not needed.
    end
end
```

then the inner loop will run slower than normal because at each iteration, a new slab of size `N` bytes must be freshly allocated. This should be a rare occurance, but is possible to encounter.

Do not manipulate the fields of a SlabBuffer that is in use.
