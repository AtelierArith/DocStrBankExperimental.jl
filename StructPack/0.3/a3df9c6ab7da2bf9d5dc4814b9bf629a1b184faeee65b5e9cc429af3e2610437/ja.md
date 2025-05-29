アクティブなコンテキストをキャプチャするスコープ付き値。

特定のコンテキスト `ctx::Context` でパック / アンパックするには、このパターンを使用できます：

```julia
using Base.ScopedValues

with(StructPack.context => ctx) do
  # ctxを明示的に渡さずにパック / アンパックを行います
  # ...
end
```

!!! info
    julia 1.11以前では、この定数はグローバル参照でした。

