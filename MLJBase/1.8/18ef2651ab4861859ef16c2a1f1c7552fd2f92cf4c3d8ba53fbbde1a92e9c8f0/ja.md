```
machines(N::AbstractNode [, model::Model])
```

ノード `N` の祖先グラフにあるすべてのマシンをリストし、オプションで、対応するモデルが指定された `model` と一致するマシンに制限します。

2つのモデルが*一致*するのは、同じ、または入れ子になったハイパーパラメータを持つ場合、または、より正確には、`MLJModelInterface.is_same_except(m1, m2)` が `true` の場合です。

`MLJModelInterface.is_same_except` も参照してください。
