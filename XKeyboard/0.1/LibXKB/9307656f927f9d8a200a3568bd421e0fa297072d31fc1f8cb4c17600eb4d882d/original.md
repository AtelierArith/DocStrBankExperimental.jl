Index of a modifier.

A *modifier* is a state component which changes the way keys are interpreted. A keymap defines a set of modifiers, such as Alt, Shift, Num Lock or Meta, and specifies which keys may *activate* which modifiers (in a many-to-many relationship, i.e. a key can activate several modifiers, and a modifier may be activated by several keys. Different keymaps do this differently).

When retrieving the keysyms for a key, the active modifier set is consulted; this detemines the correct shift level to use within the currently active layout (see [`xkb_level_index_t`](@ref)).

Modifier indices are consecutive. The first modifier has index 0.

Each modifier must have a name, and the names are unique. Therefore, it is safe to use the name as a unique identifier for a modifier. The names of some common modifiers are provided in the xkbcommon/xkbcommon-names.h header file. Modifier names are case-sensitive.

### See also

[`xkb_keymap_num_mods`](@ref)()
