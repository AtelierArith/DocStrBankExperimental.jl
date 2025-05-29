```
@rewrite(expr, move_factors_into_sums = true)
```

`expr`の値を返します。結果の計算のために作成された一時的な式の可変性を利用します。

入力として`Expr`がある場合は、代わりに[`rewrite_and_return`](@ref)を使用してください。

キーワード引数の説明については、[`rewrite`](@ref)を参照してください。

!!! info
    `;`の後に`move_factors_into_sums`を渡すことはサポートされていません。代わりに`,`を使用してください。

