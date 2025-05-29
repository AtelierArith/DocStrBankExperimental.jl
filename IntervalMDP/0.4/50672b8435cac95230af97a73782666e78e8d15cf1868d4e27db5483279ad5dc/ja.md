```
LTLfFormula
```

有限トレース上のLTL式 [1]。LTL式の構造については[`LTLFormula`](@ref)を参照してください。$ϕ$を式、$M$を区間マルコフ過程、$H$を時間の地平線とします。次に、長さ$H$のトレース内で$M ⊧ ϕ$を計算します。

### フィールド

  * `formula::String`: LTL式
  * `time_horizon::T`: 有限トレースの時間の地平線

[1] Giuseppe De Giacomo and Moshe Y. Vardi. 2013. Linear temporal logic and linear dynamic logic on finite traces. In Proceedings of the Twenty-Third international joint conference on Artificial Intelligence (IJCAI '13). AAAI Press, 854–860.
