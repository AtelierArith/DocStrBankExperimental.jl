```
InplaceableThunk(add!::Function, val::Thunk)
```

A wrapper for a `Thunk`, that allows it to define an inplace `add!` function.

`add!` should be defined such that: `ithunk.add!(Δ) = Δ .+= ithunk.val` but it should do this more efficently than simply doing this directly. (Otherwise one can just use a normal `Thunk`).

Most operations on an `InplaceableThunk` treat it just like a normal `Thunk`; and destroy its inplacability.
