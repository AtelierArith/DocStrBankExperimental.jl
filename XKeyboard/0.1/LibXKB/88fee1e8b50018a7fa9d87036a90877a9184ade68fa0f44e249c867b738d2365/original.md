```
xkb_state_component
```

Modifier and layout types for state objects. This enum is bitmaskable, e.g. (XKB_STATE_MODS_DEPRESSED | XKB_STATE_MODS_LATCHED) is valid to exclude locked modifiers.

In XKB, the DEPRESSED components are also known as 'base'.

| Enumerator                 | Note                                                                                                                                                                          |
|:-------------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| XKB_STATE_MODS_DEPRESSED   | Depressed modifiers, i.e. a key is physically holding them.                                                                                                                   |
| XKB_STATE_MODS_LATCHED     | Latched modifiers, i.e. will be unset after the next non-modifier key press.                                                                                                  |
| XKB_STATE_MODS_LOCKED      | Locked modifiers, i.e. will be unset after the key provoking the lock has been pressed again.                                                                                 |
| XKB_STATE_MODS_EFFECTIVE   | Effective modifiers, i.e. currently active and affect key processing (derived from the other state components). Use this unless you explicitly care how the state came about. |
| XKB_STATE_LAYOUT_DEPRESSED | Depressed layout, i.e. a key is physically holding it.                                                                                                                        |
| XKB_STATE_LAYOUT_LATCHED   | Latched layout, i.e. will be unset after the next non-modifier key press.                                                                                                     |
| XKB_STATE_LAYOUT_LOCKED    | Locked layout, i.e. will be unset after the key provoking the lock has been pressed again.                                                                                    |
| XKB_STATE_LAYOUT_EFFECTIVE | Effective layout, i.e. currently active and affects key processing (derived from the other state components). Use this unless you explicitly care how the state came about.   |
| XKB_STATE_LEDS             | LEDs (derived from the other state components).                                                                                                                               |
