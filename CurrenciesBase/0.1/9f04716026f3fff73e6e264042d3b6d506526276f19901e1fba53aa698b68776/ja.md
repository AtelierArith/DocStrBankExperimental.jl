```
majorunit(s::Symbol)   → Monetary{s}
majorunit(m::Monetary) → typeof(m)
majorunit(t::DataType) → t
```

通貨の主要単位を取得します。この関数は、シンボル、`Monetary`型、または`Monetary`オブジェクトのいずれかで呼び出すことができます。
