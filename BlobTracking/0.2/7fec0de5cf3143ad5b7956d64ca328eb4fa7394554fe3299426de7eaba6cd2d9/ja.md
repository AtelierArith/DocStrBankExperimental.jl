```
showblobs(img::AbstractMatrix{T}, result::TrackingResult, m::Measurement; rad=8, recorder=nothing, display=true) where T
```

画像に見つかったブロブをオーバーレイします

# 引数:

  * `img`: 画像
  * `result`: `TrackingResult`
  * `m`: `Measurement`
  * `rad`: 描画するブロブの半径
  * `recorder`: オプションの `Recorder`
  * `display = Base.display`: 画像を表示する関数。表示しない場合は `display=nothing` を使用します。
