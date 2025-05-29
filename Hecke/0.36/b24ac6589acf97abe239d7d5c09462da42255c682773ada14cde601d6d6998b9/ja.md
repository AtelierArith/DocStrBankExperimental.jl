```
residue_field(O::AbsSimpleNumFieldOrder, P::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, check::Bool = true) -> Field, Map
```

素イデアル $P$ の剰余体を、射影写像と共に返します。`check` が true の場合、イデアルが素であるかどうかがチェックされます。
