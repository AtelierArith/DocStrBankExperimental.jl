```
VibrationalMode(
        ν::Real, modestructure::Vector{Real}, δν::Union{Function,Real}=0.; N::Int=10,
        axis::NamedTuple{(:x,:y,:z)}=ẑ
    )
```

**ユーザー定義フィールド**

  * `ν::Real`: 周波数 [Hz]
  * `modestructure::Vector{Real}`: このモードに属するイオンの集合的な動きを記述する正規化された固有ベクトル。
  * `δν::Union{Function,Real}`: `ν` の時間依存の変動を記述する関数、または定数関数 `t -> δν` に変換される実数。
  * `N::Int`: ヒルベルト空間に含まれる最高レベル。
  * `axis::NamedTuple{(:x,:y,:z)}`: 振動の対称軸。この軸は基底ベクトル `x̂`、`ŷ` または `ẑ` のいずれかに沿っている必要があります。

**派生フィールド**

  * `shape::Vector{Int}`: 使用されるヒルベルト空間の次元を示します（`=[N+1]`）。
  * `_cnst_δν::Bool`: `δν` が定数関数であるかどうかを示すブールフラグ。

注: iᵗʰ フォック状態 (|i⟩) は `v=VibrationalMode(...); v[i]` としてインデックス指定することで取得できます。
