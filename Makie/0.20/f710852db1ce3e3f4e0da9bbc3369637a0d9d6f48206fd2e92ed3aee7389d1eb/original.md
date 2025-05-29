```
register_interaction!(parent, name::Symbol, interaction)
```

Register `interaction` with `parent` under the name `name`. The parent will call `process_interaction(interaction, event, parent)` whenever suitable events happen.

The interaction can be removed with `deregister_interaction!` or temporarily toggled with `activate_interaction!` / `deactivate_interaction!`.
