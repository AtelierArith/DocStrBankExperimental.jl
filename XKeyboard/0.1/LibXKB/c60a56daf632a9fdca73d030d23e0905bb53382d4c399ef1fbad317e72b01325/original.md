```
xkb_keymap_new_from_file(context, file, format, flags)
```

Create a keymap from a keymap file.

The file must contain a complete keymap. For example, in the XKB_KEYMAP_FORMAT_TEXT_V1 format, this means the file must contain one top level 'xkb_keymap' section, which in turn contains other required sections.

xkb_keymap

### Parameters

  * `context`: The context in which to create the keymap.
  * `file`: The keymap file to compile.
  * `format`: The text format of the keymap file to compile.
  * `flags`: Optional flags for the keymap, or 0.

### Returns

A keymap compiled from the given XKB keymap file, or NULL if the compilation failed.
