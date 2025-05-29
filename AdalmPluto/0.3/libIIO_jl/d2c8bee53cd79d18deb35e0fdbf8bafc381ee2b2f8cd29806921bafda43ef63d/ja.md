```
C_iio_context_get_description(context)
```

指定されたコンテキストの説明を取得します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context 構造体へのポインタ

# 戻り値

  * NULL で終わる文字列

# 注意

返される文字列には、現在のコンテキストに関する人間が読める情報が含まれます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga5591da0927887e88be4ef7d670cb60a9)
