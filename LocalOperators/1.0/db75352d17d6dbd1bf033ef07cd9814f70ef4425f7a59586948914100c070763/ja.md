```
support(A::LocalOperator)
```

`A`のサポートを`UnitRange`型として返します。つまり、ローカルオペレーター`A`が定義されているインデックスの範囲を返します。`A.support`または`getfield(A, :support)`と同等です。さらに[`maxsupport`](@ref)および[`minsupport`](@ref)も参照してください。
