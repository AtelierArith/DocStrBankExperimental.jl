```
should_inject(i::InjectorConfig)
```

Return whether or not we should inject.

Decision process:

  * Checks whether or not the given injector is active.
  * Checks that there are some values left to inject.
  * Rolls an `InjectorConfig.odds`-sided die; if 1, proceed, otherwise, don't do anything.
  * Checks that we're inside the scope of a function in `InjectorConfig.functions` OR that we're in a library that we're interested in. If yes, inject.
  * Defaults to not injecting.
