```
to_objective_callback_by_subgroup(::AbstractGroupCO, ECModel::AbstractEC)
```

ユーザーの特定のサブグループの目的を定量化するコールバック関数を返す関数。返される関数 objective_func は、ユーザーの AbstractVector を引数として受け取り、集約協調モデルの集約の目的を返します。

## パラメータ

ECModel : AbstractEC     研究対象の EC の協調 EC モデル。     モデルが協調的でない場合、エラーが発生します。 no*aggregator*group : AbstractGroup (オプション、デフォルト NonCooperative)     アグリゲーターが考慮されない場合の EC グループタイプ

## 戻り値

objective*callback*by_subgroup : Function     ユーザーの AbstractVector (または Set) を入力として受け取り、指定されたコミュニティの利益を出力として返す関数
