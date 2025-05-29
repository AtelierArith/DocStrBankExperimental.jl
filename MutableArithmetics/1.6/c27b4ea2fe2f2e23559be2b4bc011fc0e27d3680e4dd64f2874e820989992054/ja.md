```
rewrite_and_return(
    expr;
    move_factors_into_sums::Bool = true,
    return_is_mutable::Bool = false,
) -> Expr
```

式 `expr` を可変算術を使用して書き換え、最後の文が `expr` と同等の式を返します。

キーワード引数の説明については [`rewrite`](@ref) を参照してください。
