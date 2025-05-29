```
update(oldvar, updatevec, start::Int=1)
```

`oldvar`を`updatevec::AbstractVector`の`nvars(oldvar)`の値を使用して更新し、要素`start`から始めて新しい値を返します。

更新入力`updatevec`は自動微分要素型を持つ可能性があるため、変数型とこのメソッドは内部要素データ型の変更をサポートする必要があります。

このメソッドのデフォルト実装は、`Number`、`Vector`、および`StaticVector`型に存在します。

# 例

`Number`抽象型の`update`関数は次のとおりです。

```julia
    NLLSsolver.update(var::Number, updatevec, start=1) = var + updatevec[start]
```

!!! note
    必要なユーザー特化API関数です。

