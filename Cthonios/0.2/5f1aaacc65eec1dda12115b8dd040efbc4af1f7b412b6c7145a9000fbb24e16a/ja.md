```julia
QuasiStatic(
    start_time::Number,
    end_time::Number,
    Δt::Number
) -> Cthonios.QuasiStatic{Vector{Int64}, T, U} where {T<:Number, U<:(Vector{T} where T<:Number)}

```

`QuasiStatic`を構築するためのメソッド。`start_time` - 初期時間の値。`end_time` - シミュレーションを終了する時間。`Δt` - すべての時間ステップに使用する時間ステップ。
