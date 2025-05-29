```
calc_connected_components(data::Dict{String,<:Any}; edges::Union{Missing, Vector{<:String}}=missing, type::Union{Missing,String}=missing, check_enabled::Bool=true)::Set
```

ネットワークグラフの接続成分を計算し、各セットが接続成分であるバスIDのセットを返します。

この関数は、エッジが損傷している場合（それらを強化するオプションがある）を考慮しているため、powermodelsdistributionのこの機能の実装とは異なります。これにより、これらのエッジは負荷ブロックを計算する文脈でスイッチのように機能します。

接続成分を計算する際、デフォルトでは拡張エッジ（branch*ne、switch*inline_ne）を無視します。
