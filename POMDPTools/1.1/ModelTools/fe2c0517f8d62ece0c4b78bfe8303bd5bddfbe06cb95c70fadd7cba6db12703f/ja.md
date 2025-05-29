```
a, ai = action_info(policy, x)
```

ポリシー 'p' によって状態または信念 'x' で決定されたアクションと、そのアクションの計算から得られる情報（通常は `NamedTuple`、`Dict` または `nothing`）を含むタプルを返します。

デフォルトでは、情報として `nothing` を返します。
