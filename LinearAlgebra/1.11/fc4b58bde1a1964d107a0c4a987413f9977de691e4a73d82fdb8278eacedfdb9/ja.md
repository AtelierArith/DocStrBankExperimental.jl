```
ZeroPivotException <: Exception
```

ピボット（対角）位置にゼロがある場合に行列の因子分解/解決が発生し、進行できないときにスローされる例外です。これは行列が特異であることを意味するわけではありません：偽のゼロピボットを排除するために変数を再配置できるピボットLUのような別の因子分解に切り替えることが有益な場合があります。`info`フィールドは、ゼロピボットの位置（の1つ）を示します。
