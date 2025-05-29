```
remake_buffer(indp, oldbuffer, idxs, vals)
```

Return a copy of the buffer `oldbuffer` with at (optionally symbolic) indexes `idxs` replaced by corresponding values from `vals`. Both `idxs` and `vals` must be iterables of the same length. `idxs` may contain symbolic variables whose index in the buffer is determined using `indp`. The types of values in `vals` may not match the types of values stored at the corresponding indexes in the buffer, in which case the type of the buffer should be promoted accordingly. In general, this method should attempt to preserve the types of values stored in `vals` as much as possible. Types can be promoted for type-stability, to maintain performance. The returned buffer should be of the same type (ignoring type-parameters) as `oldbuffer`.

This method is already implemented for `oldbuffer::AbstractArray` and `oldbuffer::Tuple`, and supports static arrays as well.

The deprecated version of this method which takes a `Dict` mapping symbols to values instead of `idxs` and `vals` will dispatch to the new method. In addition if no `remake_buffer` method exists with the new signature, it will call `remake_buffer(sys, oldbuffer, Dict(idxs .=> vals))`.

Note that the new method signature allows `idxs` to be indexes, instead of requiring that they be symbolic variables. Thus, any type which implements the new method must also support indexes in `idxs`.
