```
gauss(N::Int,α::AbstractVector{<:Real},β::AbstractVector{<:Real})
gauss(α::AbstractVector{<:Real},β::AbstractVector{<:Real})
gauss(N::Int,op::Union{OrthoPoly,AbstractCanonicalOrthoPoly})
gauss(op::Union{OrthoPoly,AbstractCanonicalOrthoPoly})
```

ガウス求積法（ガウス・ゴルブ＝ウェルシュアルゴリズムとも呼ばれる）

`gauss()` は、与えられた重み関数に対して `N` 個のガウス求積ノードと重みを生成します。重み関数は、重み関数に対して直交する単項式の再帰係数 `N` によって表されます。

!!! note
    関数 `gauss` は、最大で `N = length(α) - 1` の求積点を受け入れるため、最大で `(length(α) - 1)` 点の求積法を提供します。


!!! note
    `N` が提供されない場合、`N = length(α) - 1` となります。

