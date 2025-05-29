```
@runcallable(eff)
```

は次のように翻訳されます。

```
Callable(function(args...; kwargs...)
  @insert_into_runhandlers CallableHandler(args...; kwargs...) eff
end)
```

`@insert_into_runhandlers`のおかげで、この外部ランナーは他の外部ランナーと良く組み合わせることができます。
