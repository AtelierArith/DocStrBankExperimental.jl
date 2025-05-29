```
create(basis::WaveguideBasis{Np,1}) where {Np}
create(basis::WaveguideBasis{Np,Nw},i::Int) where {Np,Nw}
```

生成演算子 $w^\dagger$ は [`WaveguideBasis`](@ref) に対して $w_i(t_k)^\dagger | \emptyset \rangle = | 1_k \emptyset \rangle_i$ を持ち、カットオフ（最大光子数 Np）を持ちます。ここで `i` は波導のインデックスです。$t_k$ は演算子の timeindex プロパティによって決定され、[`set_waveguidetimeindex!(a::WaveguideOperator,k::Int)`](@ref) によって変更できます。

# 引数

  * WaveguideBasis 型の basis は、カットオフ光子数 `Np` と波導の数 `Nw` を定義します。
  * `i` は演算子が作用する波導を決定し、`i ≤ Nw` である必要があります。もし `Nw=1` の場合、`i=1` が仮定されます（波導は1つしかありません）。

# 戻り値

[`WaveguideCreate`](@ref) ```
