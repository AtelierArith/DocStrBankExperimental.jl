```
@dropdims sum(A; dims=1)
```

`dropdims(...; dims=1)`でそのような還元をラップするマクロ。`sum(A; dims=1) do x stuff end`を可能にし、`@views`のようにコードの全ブロックで機能します。他のキーワード、例えば`reduce(...; dims=..., init=...)`は処理しません。
