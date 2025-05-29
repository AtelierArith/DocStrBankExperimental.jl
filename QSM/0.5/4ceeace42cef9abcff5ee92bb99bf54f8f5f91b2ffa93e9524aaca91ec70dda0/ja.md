```
homodyne!(
    v::AbstractArray{<:Complex{<:AbstractFloat}, N},
    u::AbstractArray{<:Complex{<:AbstractFloat}, N},
    w::AbstractArray{<:AbstractFloat, M <= N},
) -> v
```

ホモダインフィルター。

複素データのk空間にMdウィンドウを適用してフィルタリングします: `v = u / F^-1(w * F(u))`。

### 引数

  * `v::AbstractArray{<:Complex{<:AbstractFloat}, N}`:   ホモダインフィルタリングされた複素（マルチエコー）データ
  * `u::AbstractArray{<:Complex{<:AbstractFloat}, N}`:   複素（マルチエコー）データ
  * `w::AbstractArray{<:AbstractFloat, M <= N}`: インデックス `1` を中心としたk空間ウィンドウ。

### 戻り値

  * `v`: ホモダインフィルタリングされた複素（マルチエコー）データ
