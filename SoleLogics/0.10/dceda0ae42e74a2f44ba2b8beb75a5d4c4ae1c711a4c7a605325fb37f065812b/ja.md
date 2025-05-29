```
check(φ::Formula, i::Union{AbstractDict, AbstractVector}, args...)
```

`Formula`[@ref]を入力として受け取り、渡された辞書またはベクターに関連する真理値を返します。モデルチェックの際には、任意の`AbstractDict`および`AbstractVector`を解釈として使用できるようにします。

詳細は[`Formula`](@ref)を参照してください。
