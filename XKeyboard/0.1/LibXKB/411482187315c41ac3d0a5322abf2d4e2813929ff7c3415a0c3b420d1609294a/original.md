```
xkb_context_get_user_data(context)
```

Retrieves stored user data from the context.

This may be useful to access private user data from callbacks like a custom logging function.

xkb_context

### Returns

The stored user data. If the user data wasn't set, or the passed in context is NULL, returns NULL.
