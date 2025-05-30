```
restrict_dynamics(lc::LefschetzComplex, mvf::CellSubsets, lcsub::Cells)
```

Lefschetzサブコンプレックスに多重ベクトル場を制限します。

Lefschetz複体 `lc` 上の与えられた多重ベクトル場 `mvf` と、`lcsub` で表される局所的に閉じた集合によって与えられるサブコンプレックスに対して、関連するLefschetzサブコンプレックス `lcreduced` と、サブコンプレックス上の誘導された多重ベクトル場 `mvfreduced` を作成します。新しい多重ベクトル場の多重ベクトルは、元の多重ベクトルとサブコンプレックスの交差点です。
