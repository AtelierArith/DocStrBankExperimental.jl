```
xkb_consumed_mode
```

Consumed modifiers mode.

There are several possible methods for deciding which modifiers are consumed and which are not, each applicable for different systems or situations. The mode selects the method to use.

Keep in mind that in all methods, the keymap may decide to "preserve" a modifier, meaning it is not reported as consumed even if it would have otherwise.

| Enumerator            | Note                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| XKB_CONSUMED_MODE_XKB | This is the mode defined in the XKB specification and used by libX11.  A modifier is consumed if and only if it *may affect* key translation.  For example, if `Control+Alt+<Backspace>` produces some assigned keysym, then when pressing just `<Backspace>`, `Control` and `Alt` are consumed, even though they are not active, since if they *were* active they would have affected key translation.                                                                                                                                                                                     |
| XKB_CONSUMED_MODE_GTK | This is the mode used by the GTK+ toolkit.  The mode consists of the following two independent heuristics:  - The currently active set of modifiers, excluding modifiers which do not affect the key (as described for XKB*CONSUMED*MODE_XKB), are considered consumed, if the keysyms produced when all of them are active are different from the keysyms produced when no modifiers are active.  - A single modifier is considered consumed if the keysyms produced for the key when it is the only active modifier are different from the keysyms produced when no modifiers are active. |
