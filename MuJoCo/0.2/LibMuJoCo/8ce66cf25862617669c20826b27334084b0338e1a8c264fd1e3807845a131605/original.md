```
mjp_registerResourceProvider(provider)
```

Globally register a resource provider in a thread-safe manner. The provider must have a prefix that is not a sub-prefix or super-prefix of any current registered providers.  This function returns a slot number > 0 on success.
