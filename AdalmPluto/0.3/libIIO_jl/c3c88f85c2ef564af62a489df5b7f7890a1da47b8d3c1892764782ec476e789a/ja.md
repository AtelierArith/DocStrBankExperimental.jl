```
C_iio_context_get_device(context, index)
```

指定されたインデックスに存在するデバイスを取得します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context 構造体へのポインタ
  * `index::UInt32` : デバイスに対応するインデックス

# 戻り値

  * 成功した場合、iio_device 構造体へのポインタ
  * インデックスが無効で、アサーションが有効な場合、エラーがスローされます。
  * インデックスが無効で、アサーションが無効な場合、NULL が返されます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga3f2813ff34bf96c7c85dd05909f1c709)
