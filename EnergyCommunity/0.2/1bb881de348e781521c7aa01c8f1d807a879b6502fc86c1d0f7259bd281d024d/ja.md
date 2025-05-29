```
to_objective_callback_by_subgroup(::AbstractGroupNC, ECModel::AbstractEC)
```

与えられたユーザーのサブグループの目的を定量化するコールバック関数を返す関数。返される関数 objective_func は、ユーザーの AbstractVector を引数として受け取り、非協力モデルの集約の目的を返します。

## パラメータ

ECModel : AbstractEC     研究する EC の協力的 EC モデル。モデルが非協力的な場合、エラーがスローされます。

## 戻り値

objective*callback*by_subgroup : Function     AbstractVector（または Set）のユーザーを入力として受け取り、指定されたコミュニティの利益を出力として返す関数。
