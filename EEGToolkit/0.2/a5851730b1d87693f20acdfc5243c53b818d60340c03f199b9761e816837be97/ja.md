`artifact_reject(signal::TimeSeries, anoms::Vector{Integer}; epoch_length::Integer=30)`

異常ベクトル $\vec{x} \in \mathbb{N}^{n}$ は、異常やアーティファクトを含む `TimeSeries` のエポックである値を持つソートされたベクトルです。この関数は TimeSeries をセグメント化し、アーティファクトを含むすべてのエポックをフィルタリングします。
