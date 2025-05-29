`DiffCache(u::AbstractArray, N::Int = ForwardDiff.pickchunksize(length(u)); levels::Int = 1)` `DiffCache(u::AbstractArray; N::AbstractArray{<:Int})`

`u`のキャッシュのバージョンと`u`の`Dual`バージョンの両方を保存する`DiffCache`オブジェクトを構築します。これにより、前方モード自動微分を使用して事前キャッシュされたベクトルを利用できます。キーワード`levels`を使用するか、`chunk_sizes`の配列を指定することで、ネストされたADをサポートします。
