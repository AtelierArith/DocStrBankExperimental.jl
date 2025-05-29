Index of a keyboard layout.

The layout index is a state component which detemines which <em>keyboard layout</em> is active. These may be different alphabets, different key arrangements, etc.

Layout indices are consecutive. The first layout has index 0.

Each layout is not required to have a name, and the names are not guaranteed to be unique (though they are usually provided and unique). Therefore, it is not safe to use the name as a unique identifier for a layout. Layout names are case-sensitive.

Layout names are specified in the layout's definition, for example "English (US)". These are different from the (conventionally) short names which are used to locate the layout, for example "us" or "us(intl)". These names are not present in a compiled keymap.

If the user selects layouts from a list generated from the XKB registry (using libxkbregistry or directly), and this metadata is needed later on, it is recommended to store it along with the keymap.

Layouts are also called "groups" by XKB.

### See also

[`xkb_keymap_num_layouts`](@ref)() [`xkb_keymap_num_layouts_for_key`](@ref)()
