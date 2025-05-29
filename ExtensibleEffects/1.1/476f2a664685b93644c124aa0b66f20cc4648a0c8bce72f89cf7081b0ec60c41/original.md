```
@runstate eff
```

Note that unlike Callable, a State has to ensure that it is always the first outer Eff being run, as it returns the inner state as an additional argument.

If you would nest it with runcallable, e.g. like `@runstate @runcallable eff` it wouldn't work, as now the appended state is within the Callable and not directly within the State.
