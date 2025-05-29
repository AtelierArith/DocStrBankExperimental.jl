```
shortsymbol(s::Symbol)   → String
shortsymbol(m::Monetary) → String
shortsymbol(t::DataType) → String
```

通貨の短い、あいまいな、一般的に使用されるシンボルを取得します。この関数は、シンボル、`Monetary`型、または`Monetary`オブジェクトのいずれかで呼び出すことができます。
