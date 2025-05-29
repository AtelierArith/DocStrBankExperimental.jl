```
xkb_state_update_mask(state, depressed_mods, latched_mods, locked_mods, depressed_layout, latched_layout, locked_layout)
```

Update a keyboard state from a set of explicit masks.

This entry point is intended for window systems and the like, where a master process holds an [`xkb_state`](@ref), then serializes it over a wire protocol, and clients then use the serialization to feed in to their own [`xkb_state`](@ref).

All parameters must always be passed, or the resulting state may be incoherent.

The serialization is lossy and will not survive round trips; it must only be used to feed slave state objects, and must not be used to update the master state.

If you do not fit the description above, you should use [`xkb_state_update_key`](@ref)() instead. The two functions should not generally be used together.

xkb_state

### Returns

A mask of state components that have changed as a result of the update. If nothing in the state has changed, returns 0.

### See also

[`xkb_state_component`](@ref), [`xkb_state_update_key`](@ref)
