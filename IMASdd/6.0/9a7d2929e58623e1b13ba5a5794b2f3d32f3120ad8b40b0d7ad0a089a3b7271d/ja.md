```
@ddtime( X.Y )
```

時間依存配列からデータを取得します。これは次のことと同等です：

```
get_time_array(X, :Y)
```

および

```
@ddtime( X.Y = V)
```

時間依存配列にデータを設定します。これは次のことと同等です：

```
set_time_array(X, :Y, V)
```
