```
siteinds(M::Union{MPS, MPO}}, j::Integer; kwargs...)
```

MPOまたはMPSのサイト`j`で見つかったサイトインデックスをIndexSetとして返します。

オプションで、`plev`や`tags`のようなキーワード引数を使用して、プライムタグやプライムレベルをフィルタリングできます。
