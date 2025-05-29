```
echelon_form(A::MatElem{<:FieldElement}; reduced::Bool = true, shape::Symbol = :upper, trim::Bool = false)
```

行基本形 $R$ を $A$ のために返します。

# キーワード引数

  * `reduced`: ピボットを含む $R$ の列が簡約されているかどうか。デフォルトは `true` です。
  * `shape`: $R$ が上三角形（`:upper`, デフォルト）または下三角形（`:lower`）の基本形であるかどうか。
  * `trim`: デフォルトでは、$R$ は $A$ と同じ数の行を持ち、ゼロのみを含む行が含まれる可能性があります。`trim = true` の場合、これらの行は削除され、$R$ の行数は $A$ のランクと一致します。

他にも [`echelon_form_with_transformation`](@ref) を参照してください。
