```
TripolarGrid(arch::Distributed, FT::DataType = Float64; halo = (4, 4, 4), kwargs...)
```

分散アーキテクチャ上にトリポーラグリッドを構築します。分散トリポーラグリッドはY分割構成でのみサポートされているため、現時点ではj方向の分割のみがサポートされています。
