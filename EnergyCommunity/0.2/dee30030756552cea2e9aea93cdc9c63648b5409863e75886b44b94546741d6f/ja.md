```
to_utility_callback_by_subgroup(ECModel::AbstractEC, base_group_type::AbstractGroup)
```

特定のユーザーのサブグループの利益を定量化するコールバック関数を返す関数。返される関数 utility_func は、AbstractVector のユーザーを引数として受け取り、ユーザーが独立して最適化された場合のベースケースに対する利益を返します。

## パラメータ

ECModel : AbstractEC     研究対象の協調ECモデル。協調モデルでない場合はエラーがスローされます。 base*group*type : AbstractGroup     考慮すべきベースケースのタイプ no*aggregator*group : AbstractGroup (オプション、デフォルトは NonCooperative)     アグリゲーターが考慮されない場合のECグループタイプ

## 戻り値

utility*callback*by_subgroup : Function     AbstractVector (または Set) のユーザーを入力として受け取り、指定されたコミュニティの利益を出力として返す関数
