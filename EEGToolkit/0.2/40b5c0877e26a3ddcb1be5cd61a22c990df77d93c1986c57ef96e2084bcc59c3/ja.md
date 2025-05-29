`epoch(signal::TimeSeries, n::Integer, m::Integer)`

EEGのエポック `n, n+1, …, m` に対応するすべてのインデックスを含むベクトル `[x₁, …, xₖ]` を返します。インデックスを計算するためにデフォルトのサンプリングレートが使用されます。
