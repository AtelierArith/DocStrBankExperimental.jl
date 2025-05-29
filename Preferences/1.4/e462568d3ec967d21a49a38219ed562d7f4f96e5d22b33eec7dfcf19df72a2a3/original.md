```
@delete_preferences!(prefs...)
```

Convenience macro to call `delete_preferences!()` for the current package.  Defaults to setting `force=true`, since a package should have full control over itself, but not so for deleting the preferences in other packages, pending private dependencies.
