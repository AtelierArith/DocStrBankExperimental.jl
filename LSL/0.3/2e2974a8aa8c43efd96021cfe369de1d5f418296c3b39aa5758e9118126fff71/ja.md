```
resolve_byprop(prop, value; minimum = 1, timeout = LSL_FOREVER)
```

特定のプロパティに対して特定の値を持つすべてのストリームを解決します。

特定のストリームを解決することが目標である場合、このメソッドはすべてのストリームを解決してから目的のものを選択するよりも推奨されます。

一致するStreamInfoオブジェクトのベクターを返します（descフィールドは空です）。これらのいずれかは、その後インレットを開くために使用できます。

# 引数

-`prop::String`: 特定の値を持つべきStreamInfoプロパティ（例: "name", "type", "source_id", または "desc/manufaturer"）。  -`value::String`: プロパティが持つべき文字列値（例: "EEG"はtypeプロパティとして）。

# キーワード引数

-`minimum::Integer`: 少なくともこの数のストリームを返します。  -`timeout::Number`: 操作のタイムアウト（秒単位）。タイムアウトが切れると、希望する数のストリーム（おそらくゼロ）が返されます。

# 例

results = resolve_byprop("type", "EEG")                   ```
