```
wiggle_plot(image, xrec, time_axis; t_scale=1.5,
            new_fig=true)
```

wiggle_plot の地震トレース。

# 引数

  * `image::Array{T, 2}`: プロットするショットレコード
  * `xrec::Array{T, 1}`: 受信機座標
  * `time_axis::Array{T, 1}`: 時間軸
  * `t_scale::Float`: (オプション) 時間スケーリング、デフォルト=1.5。適用されるスケーリングは `(1:max_time).^t_scale`。
  * `new_fig::Bool`: (オプション) 新しい図を作成する、デフォルト=true
