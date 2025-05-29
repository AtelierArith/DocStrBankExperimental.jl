```
@runcallable(eff)
```

translates to

```
Callable(function(args...; kwargs...)
  @insert_into_runhandlers CallableHandler(args...; kwargs...) eff
end)
```

Thanks to `@insert_into_runhandlers` this outer runner can compose well with other outer runners.
