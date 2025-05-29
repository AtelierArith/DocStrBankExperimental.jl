```
predicttable(model<:UnfoldModel,events=Unfold.events(model),args...;kwargs...)
```

効率的に呼び出すためのショートカット (擬似コード) `result_to_table(predict(...))`。

予測結果を含む整然としたDataFrameを返します。すべての入力を`predict`にループしますが、実際には次のいずれかを指定した場合にのみ使用するのが理にかなっています：

`overlap = false`（デフォルト）または`epoch_to = "eventname"`。
