```
@set_preferences!(prefs...)
```

Convenience macro to call `set_preferences!()` for the current package.  Defaults to setting `force=true`, since a package should have full control over itself, but not so for setting the preferences in other packages, pending private dependencies.
