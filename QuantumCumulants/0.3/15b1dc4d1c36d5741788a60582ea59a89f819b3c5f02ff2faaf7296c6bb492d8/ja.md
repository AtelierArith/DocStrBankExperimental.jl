```
IndexedVariable <: CNumber
IndexedVariable(name::Symbol,ind::Index)
IndexedVariable(name::Symbol,ind1::Index,ind2:Index)
```

インデックス付きの記号変数。変数は（方程式が計算された後に）数値に簡単に置き換えることができます。2つの異なる [`Index`](@ref) オブジェクトを使用して IndexedVariable を呼び出すことで、[`DoubleIndexedVariable`](@ref) オブジェクトを作成できます。詳細については、[`value_map`](@ref) を参照してください。
