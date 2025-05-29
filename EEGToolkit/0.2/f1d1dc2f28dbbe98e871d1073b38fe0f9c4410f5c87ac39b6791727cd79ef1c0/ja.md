function artifact*reject(signal::TimeSeries, anom*dict::Dict{Int, Vector{Int}}; epoch*length::Integer=30, subepoch*length::Integer=5)::Vector{Vector{<:AbstractFloat}};

この関数は、アーティファクトを含むサブエポックを信号から削除します。`TimeSeries`と`Dict{Int, Vector{Int}}`、ここでは`anom_dict`（異常辞書と呼ばれる）を必要とします。

`anom_dict`は、`anom_dict[i] = [n₁, …, nₖ]`という形で理解され、これは`i`番目のエポックがサブエポック`n₁, ..., nₖ`にアーティファクトを持つことを意味します。

返り値はセグメント化された信号（`Vector{Vector<:AbstractFloat}}`）であり、その各セグメントはアーティファクトに汚染されたサブエポックが削除されたエポックに対応します。言い換えれば、`result`がこの関数の返り値を保持している場合、`result[i]`は`i`番目のエポックから汚染されたサブエポックを削除した後に残るものを含みます。エポック`i`のすべてのサブエポックがアーティファクトを含んでいる場合、`result[i]`が空である可能性があります。
