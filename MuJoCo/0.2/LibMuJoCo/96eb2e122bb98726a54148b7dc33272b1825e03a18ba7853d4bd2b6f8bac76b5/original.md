```
mjp_registerPlugin(plugin)
```

Globally register a plugin. This function is thread-safe. If an identical mjpPlugin is already registered, this function does nothing. If a non-identical mjpPlugin with the same name is already registered, an mju_error is raised. Two mjpPlugins are considered identical if all member function pointers and numbers are equal, and the name and attribute strings are all identical, however the char pointers to the strings need not be the same.
