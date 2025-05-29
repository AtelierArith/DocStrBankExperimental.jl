```julia
mutable struct Outpin{T} <: Causal.AbstractPin{T}
```

`OutPut` ピンを構築します。`Outpin` からのデータフローはピンの外側に向かっており、つまりデータは `OutPort` からそのリンクに書き込まれます。

# フィールド

  * `links::Union{Missing, Array{Causal.Link{T}, 1}} where T`: アウトピンにバウンドされたリンク。ピンに書き込まれたデータはすべてのリンクに転送されます
  * `id::Base.UUID`: 一意の識別子
