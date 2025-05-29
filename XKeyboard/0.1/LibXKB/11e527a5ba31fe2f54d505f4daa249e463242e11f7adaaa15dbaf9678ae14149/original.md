`xkb_context`

Opaque top level library context object.

The context contains various general library data and state, like logging level and include paths.

Objects are created in a specific context, and multiple contexts may coexist simultaneously. Objects from different contexts are completely separated and do not share any memory or state.
