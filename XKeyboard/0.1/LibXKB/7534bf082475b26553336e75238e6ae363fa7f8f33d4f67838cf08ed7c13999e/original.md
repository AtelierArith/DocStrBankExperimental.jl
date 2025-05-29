```
xkb_state_serialize_mods(state, components)
```

The counterpart to [`xkb_state_update_mask`](@ref) for modifiers, to be used on the server side of serialization.

This function should not be used in regular clients; please use the xkb_state_mod_*_is_active API instead.

xkb_state

### Parameters

  * `state`: The keyboard state.
  * `components`: A mask of the modifier state components to serialize. State components other than XKB_STATE_MODS_* are ignored. If XKB_STATE_MODS_EFFECTIVE is included, all other state components are ignored.

### Returns

A [`xkb_mod_mask_t`](@ref) representing the given components of the modifier state.
