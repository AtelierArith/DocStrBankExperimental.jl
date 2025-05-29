```
MarkedPoissonProcess{M,R,D}
```

任意のマーク分布を持つ均質時間ポアソン過程。

# フィールド

  * `λ::R`: イベントレート。
  * `mark_dist::D`: サンプルタイプ `M` のマーク分布。

# コンストラクタ

```
MarkedPoissonProcess{M}(λ, mark_dist)
```
