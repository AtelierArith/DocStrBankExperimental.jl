```
 inv(a::KInftyElem{T}, checked::Bool = true)  where T <: FieldElement
```

$ a $ が単位元である場合、$ a $ の逆元を返します。 'checked = false' の場合、$ a $ の可逆性はチェックされず、有理関数体の対応する逆元が返されます。
