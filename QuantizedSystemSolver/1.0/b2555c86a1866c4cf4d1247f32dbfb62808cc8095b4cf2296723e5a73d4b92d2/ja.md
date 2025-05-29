```
solInterpolated(sol::Sol{T,O},index::Int,step::Float64) where {T,O}
```

現在の解を各ステップで1つの変数に対して補間することによって新しい解を構築します。

# 引数

  * `sol::Sol{T,O}`: 解の構造体。
  * `index::Int`: 補間する変数のインデックス。
  * `step::Float64`: 新しい解を生成する際のステップサイズ。

# 戻り値

  * 各ステップサイズで1つの変数の情報を含む新しい解。
