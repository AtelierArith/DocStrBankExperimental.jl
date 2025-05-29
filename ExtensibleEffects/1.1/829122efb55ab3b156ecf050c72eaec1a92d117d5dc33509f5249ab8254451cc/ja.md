```
@runcontextmanager(eff)
```

は次のように翻訳されます。

```
ContextManager(function(cont)
  @insert_into_runhandlers ContextManagerHandler(cont) eff
end)
```

`@insert_into_runhandlers`のおかげで、この外部ランナーは他の外部ランナーと良く組み合わせることができます。
