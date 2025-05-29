```
xkb_state_serialize_layout(state, components)
```

The counterpart to [`xkb_state_update_mask`](@ref) for layouts, to be used on the server side of serialization.

This function should not be used in regular clients; please use the xkb_state_layout_*_is_active API instead.

xkb_state

### Parameters

  * `state`: The keyboard state.
  * `components`: A mask of the layout state components to serialize. State components other than XKB_STATE_LAYOUT_* are ignored. If XKB_STATE_LAYOUT_EFFECTIVE is included, all other state components are ignored.

### Returns

A layout index representing the given components of the layout state.
