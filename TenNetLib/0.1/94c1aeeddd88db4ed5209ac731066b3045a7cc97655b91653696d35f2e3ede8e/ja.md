```
mutable struct LinkProjTTN{T}
    tensors::Dict{LinkTypeTTN, ITensor}
    M::TTN{T}
end
```

TTNの異なるリンクにプロジェクタを保持します。励起状態または別の状態との重なりを計算するために必要です。

  * `tensors::Dict{LinkTypeTTN, ITensor}`: テンソルは各リンクです。
  * `M::TTN`: 投影するTTNです。
