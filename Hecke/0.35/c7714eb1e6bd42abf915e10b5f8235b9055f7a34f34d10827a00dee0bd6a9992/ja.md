```
 inv(a::OrdLocElem{T}, checked::Bool = true)  where {T <: AbsSimpleNumFieldElem}
```

$ a $ が単位である場合、$ a $ の逆要素を返します。 'checked = false' の場合、$ a $ の可逆性はチェックされず、数体の対応する逆要素が返されます。
