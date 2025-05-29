```
xkb_state_mod_mask_remove_consumed(state, key, mask)
```

Remove consumed modifiers from a modifier mask for a key.

\deprecated Use [`xkb_state_key_get_consumed_mods2`](@ref)() instead.

Takes the given modifier mask, and removes all modifiers which are consumed for that particular key (as in [`xkb_state_mod_index_is_consumed`](@ref)()).

### See also

[`xkb_state_mod_index_is_consumed`](@ref)() xkb_state
