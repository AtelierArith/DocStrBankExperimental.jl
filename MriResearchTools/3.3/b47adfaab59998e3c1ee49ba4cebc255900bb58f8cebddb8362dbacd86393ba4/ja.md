```
robustrescale(array, newmin, newmax; threshold=false, mask=trues(size(array)), datatype=Float64)
```

画像を新しい範囲に再スケーリングし、外れ値を無視します。`mask`内の値のみが再スケーリングオプションの推定に使用されます。
