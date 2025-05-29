```
要素
```

`map`を実装するコレクションのすべての要素にアクセスします。`Elements()`のエイリアスは`∗`（`\ast`）として利用可能です。このオプティックは`@o _[∗]`としても書くことができます。

```jldoctest
julia> using Accessors

julia> obj = (1,2,3);

julia> set(obj, Elements(), 0)
(0, 0, 0)

julia> modify(x -> 2x, obj, Elements())
(2, 4, 6)
```
