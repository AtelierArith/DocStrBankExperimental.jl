```
isempty(B::Bloating)
```

膨張した集合が空であるかどうかを判断します。

### 入力

  * `B` – 膨張した集合

### 出力

`true` は、ラップされた集合が空である場合。

### 注意事項

この実装は、負の膨張を無視します。負の膨張は、非空の集合を空の集合に変える可能性があります。
