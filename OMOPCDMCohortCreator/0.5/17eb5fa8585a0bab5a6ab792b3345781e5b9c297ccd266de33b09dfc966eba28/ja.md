GenerateGroupCounts(data::DataFrame)

DataFrame内のデータに基づいて、DataFrame内で見つかった各特徴に基づくグループカウントを取得し、プライバシー集約の目的で`person_id`を削除します。

# 引数:

  * `data::DataFrame` - 少なくとも`person_id`列を持つ必要があるDataFrame

# 戻り値:

  * `df::DataFrame` - プライバシーのために`person_id`フィールドが削除された、`data`内で見つかった各特徴に基づくグループカウントを含むDataFrame
