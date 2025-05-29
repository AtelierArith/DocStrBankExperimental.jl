```
default_structure(instantiation::StochasticInstantiation, optimizer)
```

指定された `instantiation` と `optimizer` に基づいて `StochasticInstantiation` を返します。明示的な `instantiation` が提供されている場合は、常にそれが優先されます。そうでない場合、`instantiation` が `UnspecifiedInstantiation` の場合は、オプティマイザによって要求された構造を返します。オプティマイザが提供されていない場合は、デフォルトで `Deterministic` になります。
