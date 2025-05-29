アクティブパワー表現を時間系列パラメータによって制限するための制約を作成するための構造体。詳細については、[Device Formulations](@ref formulation_intro)を確認してください。

指定された制約はUpperBound表現に依存しますが、その最も基本的な定式化は次の形式です：

$$
p_t \le \text{ActivePowerTimeSeriesParameter}_t, \quad \forall t \in \{1,\dots,T\}
$$
