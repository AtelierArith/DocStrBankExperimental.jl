```
xkb_context_include_path_reset_defaults(context)
```

Reset the context's include path to the default.

Removes all entries from the context's include path, and inserts the default paths.

xkb_context

### Returns

1 on success, or 0 if the primary include path could not be added.
