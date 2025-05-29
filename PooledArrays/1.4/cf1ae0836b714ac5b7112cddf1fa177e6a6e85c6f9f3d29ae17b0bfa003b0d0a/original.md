```
PooledArray(array, [reftype]; signed=false, compress=false)
```

Freshly allocate `PooledArray` using the given array as a source where each element will be referenced as an integer of the given type.

If `reftype` is not specified then `PooledArray` constructor is not type stable. In this case Boolean keyword arguments `signed` and `compress` determine the type of integer references. By default (`signed=false`), unsigned integers are used, as they have a greater range. However, the Arrow standard at https://arrow.apache.org/, as implemented in the Arrow package, requires signed integer types, which are provided when `signed=true`. When `compress=false`, `reftype` is a 32-bits type (`UInt32` for unsigned, `Int32` for signed); when `compress=true`, `reftype` is chosen to be the smallest integer type that is large enough to hold all unique values in `array`.

Note that if you hold mutable objects in `PooledArray` it is not allowed to modify them after they are stored in it.

In order to improve performance of `getindex` and `copyto!` operations `PooledArray`s may share pools. This sharing is automatically undone by copying a shared pool before adding new values to it.

It is not safe to assign values that are not already present in a `PooledArray`'s pool from one thread while either reading or writing to the same array from another thread (even if pools are not shared). However, reading and writing from different threads is safe if all values already exist in the pool.
