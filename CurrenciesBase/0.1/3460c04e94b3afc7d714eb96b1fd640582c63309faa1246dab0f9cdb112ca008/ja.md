```
longsymbol(s::Symbol)   → String
longsymbol(m::Monetary) → String
longsymbol(t::DataType) → String
```

通貨の一般的に使用されるシンボルを取得し、曖昧さがないように十分に区別されるようにします。この関数は、シンボル、`Monetary`型、または`Monetary`オブジェクトのいずれかで呼び出すことができます。
