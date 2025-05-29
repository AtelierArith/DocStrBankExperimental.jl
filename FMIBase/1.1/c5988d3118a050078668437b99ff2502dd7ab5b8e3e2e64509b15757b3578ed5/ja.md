```
FMUInputFunction(inputFunction, vrs)
```

FMUのインプレース入力関数のための構造体コンテナ。

# 引数

  * `inputFunction`: 新しい入力が必要なときに呼び出されるインプレース入力関数で、*入力関数パターン*の下で説明されているパターンのいずれかに一致する必要があります。
  * `vrs::AbstractVector`: 入力関数によって設定される値参照のベクター

## 入力関数パターン

利用可能な入力パターンは [`c`: 現在のコンポーネント, `u`: 現在の状態, `t`: 現在の時間, 値を配列として返し、`fmi2SetReal(..., inputValueReferences, inputFunction(...))` または `fmi3SetFloat64` に渡される]:

  * `inputFunction(t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, u::AbstractVector{<:Real})`
  * `inputFunction(x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`
