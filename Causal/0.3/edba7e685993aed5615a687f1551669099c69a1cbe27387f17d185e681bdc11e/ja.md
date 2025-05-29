```julia
mutable struct Inpin{T} <: Causal.AbstractPin{T}
```

`InPin`ピンを構築します。`Inpin`からのデータフローはピンに向かって内向きであり、つまりデータは`InPort`のリンクから読み取られます。

# フィールド

  * `link::Union{Missing, Causal.Link{T}} where T`: inpinにバウンドされたリンク。入力から読み取られるデータはリンクから読み取られます。
  * `id::Base.UUID`: 一意の識別子
