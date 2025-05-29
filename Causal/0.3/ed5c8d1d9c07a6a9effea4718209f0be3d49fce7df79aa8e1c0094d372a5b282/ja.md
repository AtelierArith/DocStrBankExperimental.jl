```julia
mutable struct Clock{T, CB}
```

`Clock`はシステムをサンプリングするための時間の瞬間を生成します。`Clock`は反復可能です。

# フィールド

  * `generator::Any`: 内部ジェネレーター。任意の反復可能なもの
  * `paused::Bool`: trueの場合、時計の反復が停止します
  * `callbacks::Any`: コールバックセット。[`Callback`](@ref)を参照してください
  * `name::Symbol`: 時計の名前
  * `uuid::Base.UUID`: 時計の識別番号

# 例

```jldoctest
julia> clk = Clock(0 : 2) 
Clock(gen:0:2, paused:false)

julia> for t in clk 
       @show t 
       end 
t = 0
t = 1
t = 2
```
