```
domainspace(op::Operator)
```

`op`のドメイン空間を返します。すなわち、`op*f`は最初に`f`を空間`domainspace(op)`の`Fun`に変換してから演算子を適用します。
