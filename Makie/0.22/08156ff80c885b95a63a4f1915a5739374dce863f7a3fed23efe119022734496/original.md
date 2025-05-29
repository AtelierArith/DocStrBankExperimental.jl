```
register_interaction!(interaction::Function, parent, name::Symbol)
```

Register `interaction` with `parent` under the name `name`. The parent will call `process_interaction(interaction, event, parent)` whenever suitable events happen. This form with the first `Function` argument is especially intended for `do` syntax.

The interaction can be removed with `deregister_interaction!` or temporarily toggled with `activate_interaction!` / `deactivate_interaction!`.
