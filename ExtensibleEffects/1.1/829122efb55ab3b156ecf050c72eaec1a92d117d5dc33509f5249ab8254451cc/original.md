```
@runcontextmanager(eff)
```

translates to

```
ContextManager(function(cont)
  @insert_into_runhandlers ContextManagerHandler(cont) eff
end)
```

Thanks to `@insert_into_runhandlers` this outer runner can compose well with other outer runners.
