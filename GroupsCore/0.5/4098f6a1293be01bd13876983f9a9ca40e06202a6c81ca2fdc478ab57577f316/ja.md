```
order(m::MonoidElement)
order(::Type{T}, m::MonoidElement) where T
```

`m`の順序を`T`のインスタンスとして返します。`m`が無限の順序の場合、`GroupsCore.InfiniteOrder`例外がスローされます。

!!! warning
    数学的に正しい答えを返すためには、任意のサイズの整数のみが必要です。

