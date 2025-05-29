```
settime(time::AbstractArray, step; start, stop, reftype, rotation)
```

列の時間値を、均一な長さの離散化された時間期間を表すための [`ScaledArray`](@ref) に変換します。`rotation` が指定されている場合（時間値が複数の回転グループに属する）、`time` フィールドが [`ScaledArray`](@ref) である [`RotatingTimeArray`](@ref) が返されます。返される配列は、相対時間に関わる操作（例えば [`lag`](@ref) や [`diff`](@ref)）のために、明確に定義された時間間隔を保証します。詳細は [`aligntime`](@ref) を参照してください。

# 引数

  * `time::AbstractArray`: 時間値を含む配列。
  * `step=nothing`: 各時間間隔の長さ；指定されていない場合は `step=one(eltype(time))` を試してください。

# キーワード

  * `start=nothing`: 返される [`ScaledArray`](@ref) のプールの最初の要素。
  * `stop=nothing`: 返される [`ScaledArray`](@ref) のプールの最後の要素。
  * `reftype::Type{<:Signed}=Int32`: [`ScaledArray`](@ref) の参照値の要素型。
  * `rotation=nothing`: 回転サンプリングデザインにおける回転グループ。
