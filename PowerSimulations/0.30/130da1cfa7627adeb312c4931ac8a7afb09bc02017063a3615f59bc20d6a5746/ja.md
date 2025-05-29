ACブランチフローがネットワークモデルに依存する制約を作成するための構造体。詳細については、[Branch Formulations](@ref PowerSystems.Branch-Formulations)を確認してください。

指定された制約は、選択されたネットワークモデルに依存します。最も一般的なアプリケーションは、PTDFネットワークモデルにおけるStaticBranchです：

$$
f_t = \sum_{i=1}^N \text{PTDF}_{i,b} \cdot \text{Bal}_{i,t}, \quad \forall t \in \{1,\dots, T\}
$$
