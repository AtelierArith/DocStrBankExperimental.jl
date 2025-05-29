```
xkb_state_match
```

Match flags for [`xkb_state_mod_indices_are_active`](@ref)() and [`xkb_state_mod_names_are_active`](@ref)(), specifying the conditions for a successful match. XKB_STATE_MATCH_NON_EXCLUSIVE is bitmaskable with the other modes.

| Enumerator                    | Note                                                                                                             |
|:----------------------------- |:---------------------------------------------------------------------------------------------------------------- |
| XKB_STATE_MATCH_ANY           | Returns true if any of the modifiers are active.                                                                 |
| XKB_STATE_MATCH_ALL           | Returns true if all of the modifiers are active.                                                                 |
| XKB_STATE_MATCH_NON_EXCLUSIVE | Makes matching non-exclusive, i.e. will not return false if a modifier not specified in the arguments is active. |
