```
buildcircuit(
  hilbert::Vector{<:Index},
  circuit::Union{Tuple, Vector{<:Any}};
  noise::Union{Nothing, Tuple, NamedTuple} = nothing
)
buildcircuit(M::Union{MPS,MPO,ITensor}, args...; kwargs...)
```

遅延表現から `ITensor` のベクトルに回路をコンパイルします。例えば、回路のゲート要素 `("gn", (i,j))` は、`hilbert` の `i` および `j` 要素に対応するランク4テンソルに変換されます。

`noise` が渡されると、対応するクラウス演算子が回路内のゲートの後に適切に挿入されます。
