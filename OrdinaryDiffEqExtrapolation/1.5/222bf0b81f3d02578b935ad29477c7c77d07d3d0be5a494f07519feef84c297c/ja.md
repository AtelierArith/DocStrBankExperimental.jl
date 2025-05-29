```julia
AitkenNeville(; max_order::Int = 10,
                min_order::Int = 1,
                init_order = 3,
                thread = OrdinaryDiffEq.False())
```

並列化された明示的外挿法。Aitken-Nevilleを使用したオイラー外挿法で、ロンバーグ列を使用します。

### キーワード引数

  * `max_order`: 適応順序アルゴリズムの最大順序。
  * `min_order`: 適応順序アルゴリズムの最小順序。
  * `init_order`: 適応順序アルゴリズムの初期順序。
  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャストを直列（`thread = OrdinaryDiffEq.False()`）にするか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。

## 参考文献

@inproceedings{elrod2022parallelizing,   title={Parallelizing explicit and implicit extrapolation methods for ordinary differential equations},   author={Elrod, Chris and Ma, Yingbo and Althaus, Konstantin and Rackauckas, Christopher and others},   booktitle={2022 IEEE High Performance Extreme Computing Conference (HPEC)},   pages={1–9},   year={2022},   organization={IEEE}}
