```
wavelet(c[, t=WT.Filter][, boundary=WT.Periodic][, s=Real])
```

波レットタイプを構築します。ここで、`c`は波レットクラス、`t`は変換タイプ（`WT.Filter`または`WT.Lifting`）、`boundary`は境界処理のタイプです。連続の場合、s>0はオクターブ$2^J$と$2^{J+1}$の間の波レットの数（デフォルトは8で、音楽や他の音声に最も適しています）。

# 例

```julia
wavelet(WT.coif6)
wavelet(WT.db1, WT.Lifting)
wavelet(WT.morl,4)
```

**参照:** `WT.WaveletClass`
