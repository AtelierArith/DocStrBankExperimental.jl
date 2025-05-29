```
クイックチェック
```

ランダム入力の生成を通じてチェックするプロパティのセットを含みます。

# フィールド

  * `description::AbstractString`: インスタンスの説明
  * `rng::AbstractRNG`: 入力を生成するために使用される擬似乱数生成器
  * `predicates::PredsAssoc`: チェックするための述語
  * `variables::ArgsDict`: 述語によって使用される引数
  * `n::Int`: 生成するランダム入力の数
  * `serialize_fails::Bool`: trueの場合、失敗した入力をJLSOファイルにシリアライズする
