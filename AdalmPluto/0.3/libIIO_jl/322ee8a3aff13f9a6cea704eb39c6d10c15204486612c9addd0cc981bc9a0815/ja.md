```
C_iio_context_get_name(context)
```

指定されたコンテキストの名前を取得します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context 構造体へのポインタ

# 戻り値

  * NULL で終わる文字列

# 注意

返される文字列は、コンテキストがそれぞれローカル、xml、およびネットワークバックエンドで作成された場合、ローカル、xml、またはネットワークになります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gafed8e036873ad6f70c3db92c7136ad31)
