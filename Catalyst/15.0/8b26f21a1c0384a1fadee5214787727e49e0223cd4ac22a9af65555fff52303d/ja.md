```
isdetailedbalanced(rs::ReactionSystem, parametermap; reltol=1e-9, abstol)
```

運動系（反応ネットワークと一連の反応速度定数を持つ）に詳細平衡の平衡解が存在するかどうかを、Wegscheider条件を使用して構成的に計算します。[Feinberg, 1989](https://www.sciencedirect.com/science/article/pii/0009250989851243)。詳細平衡解とは、すべての前進反応の速度がその逆反応と正確に等しい解のことです。辞書、ベクトル、または変数から値へのマッピングのタプルを受け入れます。例：[k1 => 1.0, k2 => 2.0,...]。
