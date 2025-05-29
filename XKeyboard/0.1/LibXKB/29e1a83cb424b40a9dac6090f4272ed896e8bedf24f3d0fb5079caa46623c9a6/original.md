A number used to represent a physical key on a keyboard.

A standard PC-compatible keyboard might have 102 keys. An appropriate keymap would assign each of them a keycode, by which the user should refer to the key throughout the library.

Historically, the X11 protocol, and consequentially the XKB protocol, assign only 8 bits for keycodes. This limits the number of different keys that can be used simultaneously in a single keymap to 256 (disregarding other limitations). This library does not share this limit; keycodes beyond 255 ('extended keycodes') are not treated specially. Keymaps and applications which are compatible with X11 should not use these keycodes.

The values of specific keycodes are determined by the keymap and the underlying input system. For example, with an X11-compatible keymap and Linux evdev scan codes (see linux/input.h), a fixed offset is used:

The keymap defines a canonical name for each key, plus possible aliases. Historically, the XKB protocol restricts these names to at most 4 (ASCII) characters, but this library does not share this limit.

```c++
 xkb_keycode_t keycode_A = KEY_A + 8;
```

### See also

[`xkb_keycode_is_legal_ext`](@ref)() [`xkb_keycode_is_legal_x11`](@ref)()
