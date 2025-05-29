```
variance(ito::ItoIntegral, from::Real, to::Real)
variance(ito::ItoIntegral, base::Union{Date,DateTime}, from::Union{Date,DateTime}, to::Union{Date,DateTime})
```

`ItoIntegral`のある時点から別の時点までの分散を取得します。

### 入力

  * `ito` - 分散を求めたい`ItoIntegral`。
  * `from` - 積分が開始される時刻。
  * `to` - 積分が終了する時刻。

### 出力

  * スカラー
