Index of a shift level.

Any key, in any layout, can have several <em>shift levels</em>. Each shift level can assign different keysyms to the key. The shift level to use is chosen according to the current keyboard state; for example, if no keys are pressed, the first level may be used; if the Left Shift key is pressed, the second; if Num Lock is pressed, the third; and many such combinations are possible (see [`xkb_mod_index_t`](@ref)).

Level indices are consecutive. The first level has index 0.
