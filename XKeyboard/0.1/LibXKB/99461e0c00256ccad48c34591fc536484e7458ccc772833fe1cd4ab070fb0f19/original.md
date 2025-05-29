Index of a keyboard LED.

LEDs are logical objects which may be *active* or *inactive*. They typically correspond to the lights on the keyboard. Their state is determined by the current keyboard state.

LED indices are non-consecutive. The first LED has index 0.

Each LED must have a name, and the names are unique. Therefore, it is safe to use the name as a unique identifier for a LED. The names of some common LEDs are provided in the xkbcommon/xkbcommon-names.h header file. LED names are case-sensitive.

!!! warning
    A given keymap may specify an exact index for a given LED. Therefore, LED indexing is not necessarily sequential, as opposed to modifiers and layouts. This means that when iterating over the LEDs in a keymap using e.g. [`xkb_keymap_num_leds`](@ref)(), some indices might be invalid. Given such an index, functions like [`xkb_keymap_led_get_name`](@ref)() will return NULL, and [`xkb_state_led_index_is_active`](@ref)() will return -1.


LEDs are also called "indicators" by XKB.

### See also

[`xkb_keymap_num_leds`](@ref)()
