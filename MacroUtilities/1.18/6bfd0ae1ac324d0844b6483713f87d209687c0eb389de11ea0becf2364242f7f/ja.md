```
@return_if_exception(ex)
```

デストラクチャリング代入式 `ex` を評価します。形式は `(; names...) = rhs` または `(names...) = rhs` であり、`rhs` が `Exception` を返す場合は現在の関数から戻ります。
