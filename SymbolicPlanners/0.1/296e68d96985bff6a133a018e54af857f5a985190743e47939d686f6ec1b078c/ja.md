```
HSPHeuristic(op::Function)
```

リラックスした計画グラフヒューリスティックのファミリーで、HSPプランナーによって導入されました[1]。このヒューリスティックは、すべてのグラウンドアクションと計画に関連する条件の間の依存関係を格納するグラフを事前に計算します。各アクション（および目標）を達成するコストは、アクションまたは目標が依存する各（前）条件を達成するためのコストの合計として再帰的に推定されます。ここで、`op`は集約関数（例：`max`または`+`）です。

次に、各条件（いわゆる「事実」）を達成するコストは、その条件を達成するすべてのアクションの中での最小コストとして推定されます。アクションによって条件が達成されると、それはプロセスの残りの間真であると見なされるため、ヒューリスティックのリラックスした性質があります。

この実装は、負の前提条件、選択的前提条件（すなわち、`or`、`exists`）、および機能的前提条件（例：数値比較、または他のブール値関数の非ブール流体）を持つドメインをサポートします。機能的前提条件は、構成要素の流体が何らかのアクションによって変更されると、楽観的に真になると仮定することによって処理されます。

[1] B. Bonet and H. Geffner, "Planning as Heuristic Search," Artificial Intelligence, vol. 129, no. 1, pp. 5–33, Jun. 2001, [https://doi.org/10.1016/S0004-3702(01)00108-4](https://doi.org/10.1016/S0004-3702(01)00108-4).
