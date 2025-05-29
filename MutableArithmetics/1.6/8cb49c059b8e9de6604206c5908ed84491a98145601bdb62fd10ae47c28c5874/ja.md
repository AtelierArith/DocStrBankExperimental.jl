```
rewrite(
    expr;
    move_factors_into_sums::Bool = true,
    return_is_mutable::Bool = false,
) -> Tuple{Symbol,Expr[,Bool]}
```

式 `expr` を可変算術を使用するように書き換えます。

`expr` に相当する `gensym` された変数と、その変数を作成するために必要なコードからなる `(variable, code)` を返します。

## `move_factors_into_sums`

`move_factors_into_sums = true` の場合、いくつかの項は、総和が線形関数を生成するという仮定に基づいて書き換えられます。

例えば、`move_factors_into_sums = true` の場合、`y * sum(x[i] for i in 1:2)` は次のように書き換えられます：

```julia
variable = MA.Zero()
for i in 1:2
    variable = MA.operate!!(MA.add_mul, result, y, x[i])
end
```

`move_factors_into_sums = false` の場合、次のように書き換えられます：

```julia
term = MA.Zero()
for i in 1:2
    term = MA.operate!!(MA.add_mul, term, x[i])
end
variable = MA.operate!!(*, y, term)
```

後者は、`add_mul` に効率的なフォールバックがあり、`*(y, term)` に対してはない場合、追加のアロケーションを生成する可能性があります。

## `return_is_mutable`

`return_is_mutable = true` の場合、この関数は3つの引数を返します。3つ目は、返された式がユーザーの元の式を変更することなく安全に変更できるかどうかを示す `Bool` です。

`move_factors_into_sums = true` の場合、`return_is_mutable` は `true` にはできません。
