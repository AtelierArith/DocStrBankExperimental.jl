```
destroy(basis::WaveguideBasis{Np,1}) where {Np}
destroy(basis::WaveguideBasis{Np,Nw},i::Int) where {Np,Nw}
```

消滅演算子 $w$ は [`WaveguideBasis`](@ref) に対して $w_i(t_k) | 1_j \emptyset \rangle_i = \delta_{k,j} | \emptyset \rangle$ であり、カットオフ（最大光子数 Np）を持ち、`i` は波導のインデックスです。$t_k$ は演算子の timeindex プロパティによって決定され、[`set_waveguidetimeindex!(a::WaveguideOperator,k::Int)`](@ref) によって変更可能です。

# 引数

  * WaveguideBasis 型の basis は、カットオフ光子数 `Np` と波導の数 `Nw` を定義します。
  * `i` は演算子が作用する波導を決定し、`i ≤ Nw` である必要があります。もし `Nw=1` の場合、`i=1` が仮定されます（波導は1つしかありません）。

# 戻り値

[`WaveguideDestroy`](@ref)
