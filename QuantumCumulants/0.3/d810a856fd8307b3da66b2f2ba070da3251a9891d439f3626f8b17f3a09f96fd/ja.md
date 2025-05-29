```
Index(hilb::HilbertSpace,name::Symbol,range::Union{Int64,Sym},aon::Int)
```

インデックスを定義します。名前としてSymbolを使用し、計算と交換子関係のために[`HilbertSpace`](@ref)を使用します。同じフィールドを持つインデックスは等しいと見なされます。詳細については、[`IndexedOperator`](@ref)および[`IndexedVariable`](@ref)を参照してください。

# フィールド:

  * hilb: インデックスが定義される全体の[`HilbertSpace`](@ref)。
  * name: インデックスの名前を定義し、[`IndexedOperator`](@ref)の積項がどのように順序付けられるか（アルファベット順）を定義するSymbol。
  * range: インデックスの上限制限。これはSymbolicUitls.Symbolicまたは任意の数値である可能性があります。
  * aon: インデックスが作用する特定の[`HilbertSpace`](@ref)を指定する数値。
