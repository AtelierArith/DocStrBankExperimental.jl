A number used to represent the symbols generated from a key on a keyboard.

A key, represented by a keycode, may generate different symbols according to keyboard state. For example, on a QWERTY keyboard, pressing the key labled <A> generates the symbol 'a'. If the Shift key is held, it generates the symbol 'A'. If a different layout is used, say Greek, it generates the symbol 'α'. And so on.

Each such symbol is represented by a keysym. Note that keysyms are somewhat more general, in that they can also represent some "function", such as "Left" or "Right" for the arrow keys. For more information, see: https://www.x.org/releases/current/doc/xproto/x11protocol.html#keysym_encoding

Specifically named keysyms can be found in the xkbcommon/xkbcommon-keysyms.h header file. Their name does not include the XKB_KEY_ prefix.

Besides those, any Unicode/ISO 10646 character in the range U0100 to U10FFFF can be represented by a keysym value in the range 0x01000100 to 0x0110FFFF. The name of Unicode keysyms is "U<codepoint>", e.g. "UA1B2".

The name of other unnamed keysyms is the hexadecimal representation of their value, e.g. "0xabcd1234".

Keysym names are case-sensitive.
