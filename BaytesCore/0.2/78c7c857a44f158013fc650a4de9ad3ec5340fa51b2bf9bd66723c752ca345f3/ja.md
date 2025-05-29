```julia
struct SubSampled <: BaytesCore.DataStructure
```

推論のためにデータをサブサンプリングできるかどうかを決定します。

# フィールド

  * `buffer::Vector{Int64}`: サブサンプリングされたインデックスのバッファインデックス。
