Construct a `Keymap` via X11 using `conn` as the connection to an X Server.

This action uses XKB, the X Keyboard extension, which must be initialized for each X11 connection, typically when creating a keymap. If this is not your first call to this constructor with this connection, you should set `setup_xkb` to `false`.

!!! warning



Upon creation, the keymap state (e.g. active modifiers) is filled with the current state. That means, if you press    shift down while executing this code, the keymap state will encode a state where the shift modifier is active.    This is not a concern if the state is properly managed by the calling code, e.g. XCB.jl updating the keymap on key presses    and key releases, but this is something to be aware of.
