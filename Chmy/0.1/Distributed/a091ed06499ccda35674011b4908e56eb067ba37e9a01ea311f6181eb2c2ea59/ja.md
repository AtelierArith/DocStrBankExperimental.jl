```
BoundaryConditions.bc!(side::Side, dim::Dim,
                            arch::DistributedArchitecture,
                            grid::StructuredGrid,
                            batch::ExchangeBatch)
```

分散グリッドに境界条件を適用し、内部でハロ交換が行われます。

# 引数

  * `side`: ハロ交換が行われるグリッドの側面。
  * `dim`: ハロ交換が行われる次元。
  * `arch`: 通信に使用される分散アーキテクチャ。
  * `grid`: ハロ交換が行われる構造化グリッド。
  * `batch`: 境界条件を適用するために設定されたバッチ。
