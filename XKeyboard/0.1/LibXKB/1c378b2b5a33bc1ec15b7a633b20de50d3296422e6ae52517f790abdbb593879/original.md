```
xkb_state_update_key(state, key, direction)
```

Update the keyboard state to reflect a given key being pressed or released.

This entry point is intended for programs which track the keyboard state explicitly (like an evdev client). If the state is serialized to you by a master process (like a Wayland compositor) using functions like [`xkb_state_serialize_mods`](@ref)(), you should use [`xkb_state_update_mask`](@ref)() instead. The two functions should not generally be used together.

A series of calls to this function should be consistent; that is, a call with XKB_KEY_DOWN for a key should be matched by an XKB_KEY_UP; if a key is pressed twice, it should be released twice; etc. Otherwise (e.g. due to missed input events), situations like "stuck modifiers" may occur.

This function is often used in conjunction with the function [`xkb_state_key_get_syms`](@ref)() (or [`xkb_state_key_get_one_sym`](@ref)()), for example, when handling a key event. In this case, you should prefer to get the keysyms *before* updating the key, such that the keysyms reported for the key event are not affected by the event itself. This is the conventional behavior.

xkb_state

### Returns

A mask of state components that have changed as a result of the update. If nothing in the state has changed, returns 0.

### See also

[`xkb_state_update_mask`](@ref)()
