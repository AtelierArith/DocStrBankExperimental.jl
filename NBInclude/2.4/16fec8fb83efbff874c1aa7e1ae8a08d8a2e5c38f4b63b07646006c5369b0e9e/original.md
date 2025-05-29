```
nbinclude(m::Module, path; ...)
```

Like `@nbinclude(path; ...)` but allows you to specify a module to evaluate in, similar to `include(m, path)`.
