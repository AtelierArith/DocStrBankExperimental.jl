```
HardCutoffSD(J::AbstractSD, ωcutoff)
```

基底のスペクトル密度 `J` と指定された周波数カットオフ `ωcutoff` を使用して、ハード周波数カットオフを持つスペクトル密度を構築します。

# 引数

  * `J::AbstractSD`: 基底のスペクトル密度。
  * `ωcutoff::Float64`: 周波数カットオフ。

# 戻り値

  * ハード周波数カットオフを持つスペクトル密度を表す `HardCutoffSD` 構造体のインスタンス。
