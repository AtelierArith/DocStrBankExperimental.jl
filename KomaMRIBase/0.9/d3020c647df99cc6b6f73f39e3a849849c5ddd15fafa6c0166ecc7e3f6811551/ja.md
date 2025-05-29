```
obj = Phantom(name, x, y, z, ρ, T1, T2, T2s, Δw, Dλ1, Dλ2, Dθ, motion)
```

Phantom構造体。ほとんどのフィールド名はベクトルであり、各要素はスピンを表すプロパティ値に関連付けられています。この構造体はシミュレーションの入力として機能します。

# 引数

  * `name`: (`::String`) ファントム名
  * `x`: (`::AbstractVector{T<:Real}`, `[m]`) スピンx位置ベクトル
  * `y`: (`::AbstractVector{T<:Real}`, `[m]`) スピンy位置ベクトル
  * `z`: (`::AbstractVector{T<:Real}`, `[m]`) スピンz位置ベクトル
  * `ρ`: (`::AbstractVector{T<:Real}`) スピンプロトン密度ベクトル
  * `T1`: (`::AbstractVector{T<:Real}`, `[s]`) スピンT1パラメータベクトル
  * `T2`: (`::AbstractVector{T<:Real}`, `[s]`) スピンT2パラメータベクトル
  * `T2s`: (`::AbstractVector{T<:Real}`, `[s]`) スピンT2sパラメータベクトル
  * `Δw`: (`::AbstractVector{T<:Real}`, `[rad/s]`) スピンオフレゾナンスパラメータベクトル
  * `Dλ1`: (`::AbstractVector{T<:Real}`) スピンDλ1（拡散）パラメータベクトル
  * `Dλ2`: (`::AbstractVector{T<:Real}`) スピンDλ2（拡散）パラメータベクトル
  * `Dθ`: (`::AbstractVector{T<:Real}`) スピンDθ（拡散）パラメータベクトル
  * `motion`: (`::Union{NoMotion, Motion{T<:Real} MotionList{T<:Real}}`) モーション

# 戻り値

  * `obj`: (`::Phantom`) Phantom構造体

# 例

```julia-repl
julia> obj = Phantom(x=[0.0])

julia> obj.ρ
```
