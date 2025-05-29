```
to_objective_callback_by_subgroup(::AbstractGroupANC, ECModel::AbstractEC)
```

与えられたユーザーのサブグループの目的を定量化するコールバック関数を返す関数。返される関数 objective_func は、ユーザーの AbstractVector を引数として受け取り、集約非協力モデルの集約の目的を返します。

## パラメータ

ECModel : AbstractEC     研究対象の EC の協力 EC モデル。     モデルが非協力的な場合、エラーがスローされます。 base_model : AbstractEC オプション     提供されると、計算を行うために使用されるベースモデルを表します。

## 戻り値

objective*callback*by_subgroup : 関数     ユーザーの AbstractVector (または Set) を入力として受け取り、指定されたコミュニティの利益を出力として返す関数です。
