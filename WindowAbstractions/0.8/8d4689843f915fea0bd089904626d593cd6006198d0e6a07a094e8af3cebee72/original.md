Type of input or window event which may occur on a particular window.

This type is defined as a bitmask, to make it easier to work with sets of events.

```julia
struct EventType <: BitMasks.BitMask{UInt32}
```

  * `val::UInt32`
