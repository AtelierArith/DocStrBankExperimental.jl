`Linearization` 構造体は、`Delta` および `Flow` ファクタノードの近似方法を定義します。この方法は、展開点 x の周りで f の局所線形化を行います。

!!! note
    `Linearization` は微分可能な関数に対してのみうまく機能します。非微分可能な関数に対しては結果が正確でない可能性があります。


デフォルトパラメータを持つ `Linearization` 構造体は、`Linearization()` として構築できます。

`Linearization` 構造体は `DeltaMeta` または `FlowMeta` 構造体内で使用され、次のように含めることができます：

```
    y ~ f(x) where { meta = DeltaMeta(method = Linearization()) }
    # または
    y ~ Flow(x) where { meta = FlowMeta(flowmodel, Linearization()) }
```
