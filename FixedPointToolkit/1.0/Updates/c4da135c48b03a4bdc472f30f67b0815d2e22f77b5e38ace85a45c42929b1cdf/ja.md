```julia
SimpleMixing(VIn::N, VOut::N, F::T ; F_args::Tuple = (), F_kwargs::Dict = Dict() , alpha::Float64 = 0.5, _extra...) --> Dict   where {T<:Function, N<:Union{Number, Vector{<:Number}}}
```

次の内容を含む辞書を返します

  * "VInNext" : 重み (1-`alpha`) と `alpha` をそれぞれ用いた VIn と VOut の単純な混合。
  * "VOutNext" : 固定引数 `F_args` と キーワード引数 `F_kwargs` を用いて VInNExt で評価された関数 `F`。
  * "Delta" : 次の入力と出力の間のノルム差。
  * "kwargs" : 次の固定点反復での後続の関数呼び出しに使用されるこの関数自体のキーワード引数。これは単純な混合であるため、`alpha` は一定に保たれます。
