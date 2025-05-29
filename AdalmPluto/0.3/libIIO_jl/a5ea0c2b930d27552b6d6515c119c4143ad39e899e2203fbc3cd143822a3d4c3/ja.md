```
C_iio_context_clone(context)
```

既存のIIOコンテキストを複製します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context構造体へのポインタ

# 戻り値

  * 成功した場合、iio_context構造体へのポインタ
  * 失敗した場合、アサーションが有効な場合はエラーをスローし、そうでない場合はNULLを返します。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga1815e7c39b9a69aa11cf948b0433df01)
