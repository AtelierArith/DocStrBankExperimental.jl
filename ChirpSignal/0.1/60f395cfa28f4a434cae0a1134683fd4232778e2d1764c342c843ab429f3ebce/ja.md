```
chirp(T, fs, fl, fh; method="linear", phase=0.0) -> Array{Float64,1}
```

チャープスイープ周波数サインジェネレーター。

# 引数

  * `T`     : 信号の長さ（秒）
  * `fs`    : サンプリングレート
  * `fl`    : 終了時間ステップでの下限周波数, fl <= fs
  * `fh`   : 終了時間ステップでの上限周波数, fh <= fs
  * `phase` : チャープ信号の位相, sin(wt + phase)のように
  * `method`: 利用可能なメソッドは'linear','quadratic','exponential'および'logarithmic'; デフォルトは'linear'です。
