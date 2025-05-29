```
order(::Type{T} = BigInt, g::GroupElem) where T
```

$$
g
$$

の順序を`T`のインスタンスとして返します。$g$が無限の順序の場合、`InfiniteOrderError`例外がスローされます。この種の例外を避けるために`is_finite_order(G)`を使用してください。順序が型`T`に収まらない場合、`InexactError`例外がスローされます。
