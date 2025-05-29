```
dfcor(df::AbstractDataFrame, cols1=names(df), cols2=names(df), verbose=false)
```

指定された列のセット `cols1` と別のセット `cols2` によってデータフレーム内の相関を計算します。`cols1` と `cols2` の相関の直積が計算されます。
