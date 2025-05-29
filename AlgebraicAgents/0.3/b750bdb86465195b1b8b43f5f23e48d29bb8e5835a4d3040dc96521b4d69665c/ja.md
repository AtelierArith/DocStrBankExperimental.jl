```
⊕(models::Vararg{AbstractAlgebraicAgent, N}; name)
```

代数モデルの代数和。結果のモデルの名前をオプションで指定します。

デフォルトでは、`FreeAgent`のインスタンスを出力します。

# 例

```julia
⊕(m1, m2; name="diagram1") ⊕ ⊕(m3, m4; name="diagram2");
```
