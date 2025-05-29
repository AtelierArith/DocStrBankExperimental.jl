Code used by XKB to represent symbols on a logical level.

Such codes differ from keycodes in that they keycodes are stateless: when a key is pressed, it always emits the same keycode.

To understand the difference, let's take the physical key `AD01`. When pressed, it emits an integer signal (keycode) representing that specific key on the keyboard (the name `AD01` is just a label that is more friendly than an integer code). If pressed on a US keyboard (QWERTY layout), it may emit the character `q`. Or `Q`. This depends on whether a shift modifier or caps lock (without shift modifier) is active, among other things. If we were on a French keyboard, then the letter would be `a` (AZERTY layout), or `A`. if we had pressed the left or right shift key instead, we would not even have a printable character associated with the keystroke.

`q`, `Q`, `a`, `A`, `left_shift` and `right_shift` are all semantic symbols, need not be printable (e.g. shifts) and their mapping from a physical key -if one exists- depends on some external state, tracked inside a [`Keymap`](@ref). Just like physical keys, these symbols are represented with an integer code, and have a more friendly string representation that one can obtain with `String(keysym::Keysym)`.

Keysyms are not physical keys, nor input characters.
