```julia
ExtrapolationMidpointHairerWanner(; max_order = 10,
                                    min_order = 2,
                                    init_order = 5,
                                    thread = OrdinaryDiffEq.True(),
                                    sequence = :harmonic,
                                    sequence_factor = 2)
```

並列化された明示的外挿法。バリセントリック座標を使用した中点外挿で、適応性の挙動においてHairerのODEXに従います。

### キーワード引数

  * `max_order`: 適応順序アルゴリズムの最大順序。
  * `min_order`: 適応順序アルゴリズムの最小順序。
  * `init_order`: 適応順序アルゴリズムの初期順序。
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動された場合。
  * `sequence`: ステップ番号のシーケンス、または分割シーケンスとも呼ばれます。可能な値は `:harmonic`, `:romberg` または `:bulirsch` です。
  * `sequence_factor`: 内部離散化を評価する際に取るシーケンスの偶数倍を示します。

## 参考文献

@inproceedings{elrod2022parallelizing,   title={Parallelizing explicit and implicit extrapolation methods for ordinary differential equations},   author={Elrod, Chris and Ma, Yingbo and Althaus, Konstantin and Rackauckas, Christopher and others},   booktitle={2022 IEEE High Performance Extreme Computing Conference (HPEC)},   pages={1–9},   year={2022},   organization={IEEE}}
