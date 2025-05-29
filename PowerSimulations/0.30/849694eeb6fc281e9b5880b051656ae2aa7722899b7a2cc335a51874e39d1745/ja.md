アクティブ電力出力式を制限するための制約を作成する構造体。詳細については、[Device Formulations](@ref formulation_intro)を確認してください。

指定された制約はUpperBoundおよびLowerBound式に依存しますが、その最も基本的な定式化は次の形式です：

$$
P^\text{min} \le p_t^\text{out} \le P^\text{max}, \quad \forall t \in \{1,\dots,T\}
$$
