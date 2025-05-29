```
ExponentialCutoffSD(J::AbstractSD, ωcutoff)
```

基底のスペクトル密度 `J` と指定された周波数カットオフ `ωcutoff` を使用して、指数関数的周波数カットオフを持つスペクトル密度を構築します。

# 引数

  * `J::AbstractSD`: 基底のスペクトル密度。
  * `ωcutoff`: 周波数カットオフ。

# 戻り値

  * 指数関数的周波数カットオフを持つスペクトル密度を表す `ExponentialCutoffSD` 構造体のインスタンス。
