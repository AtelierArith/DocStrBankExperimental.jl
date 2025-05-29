```
to_objective_callback_by_subgroup(ECModel::AbstractEC)
```

与えられたユーザーのサブグループの目的を定量化するコールバック関数を返す関数。返される関数 objective_func は、ユーザーの AbstractVector を引数として受け取り、任意のモデルの集約の目的を返します。

## パラメータ

ECModel : AbstractEC     研究する EC の協調 EC モデル。モデルが協調的でない場合、エラーがスローされます。

## 戻り値

objective*callback*by_subgroup : 関数     ユーザーの AbstractVector (または Set) を入力として受け取り、指定されたコミュニティの利益を出力として返す関数です。
