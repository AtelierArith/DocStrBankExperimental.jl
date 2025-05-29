```
xkb_keymap_key_repeats(keymap, key)
```

Determine whether a key should repeat or not.

A keymap may specify different repeat behaviors for different keys. Most keys should generally exhibit repeat behavior; for example, holding the 'a' key down in a text editor should normally insert a single 'a' character every few milliseconds, until the key is released. However, there are keys which should not or do not need to be repeated. For example, repeating modifier keys such as Left/Right Shift or Caps Lock is not generally useful or desired.

xkb_keymap

### Returns

1 if the key should repeat, 0 otherwise.
