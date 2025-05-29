```
howell_form(A::MatElem{<:RingElement}; reduced::Bool = true, shape::Symbol = :upper, trim::Bool = false)
```

行列 $A$ のハウエル形式 $H$ を返します。`base_ring(A)` が主イデアル環であると仮定します。

# キーワード引数

  * `reduced`: ピボットを含む $H$ の列が簡約されているかどうか。デフォルトは `true` です。
  * `shape`: $H$ が上右（`:upper`, デフォルト）または下左（`:lower`）のエシェロン形式であるかどうか。
  * `trim`: デフォルトでは、$H$ は $A$ と同じかそれ以上の行数を持ち、ゼロのみを含む行が含まれる可能性があります。`trim = true` の場合、これらの行は削除されます。

関連情報は [`howell_form_with_transformation`](@ref) を参照してください。
