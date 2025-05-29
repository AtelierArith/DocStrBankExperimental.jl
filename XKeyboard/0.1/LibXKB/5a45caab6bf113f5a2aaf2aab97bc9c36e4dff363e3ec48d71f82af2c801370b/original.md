`xkb_keymap`

Opaque compiled keymap object.

The keymap object holds all of the static keyboard information obtained from compiling XKB files.

A keymap is immutable after it is created (besides reference counts, etc.); if you need to change it, you must create a new one.
