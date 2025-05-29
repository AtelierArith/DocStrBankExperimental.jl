```
rheologrun(log::RheoLog, d::Union{RheoTimeData,RheoFreqData,Nothing} = nothing)
```

ログからすべてのアクションを実行します。提供されたデータ `d` にそれらを適用するか、そうでなければログの最初のアクションを使用してデータを再読み込み/再作成します。
