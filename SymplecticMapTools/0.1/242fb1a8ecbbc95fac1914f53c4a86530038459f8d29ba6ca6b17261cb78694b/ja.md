```
kernel_sample_F(F::Function, N::Integer, xb::AbstractVector,
                yb::AbstractVector)
```

Sobol サンプル `N` 点を長方形 `xb` × `yb` において生成します。次に、各点で `F` を評価します。入力は `kernel_eigs` および `kernel_bvp` に使用できます。

引数:

  * `F`: 状態空間から自身へのシンプレクティック写像
  * `N`: サンプリングする点の数
  * `xb` × `yb`: サンプリングする長方形の 2 ベクトルの境界

出力:

  * `xs`: `kernel_eigs` および `kernel_bvp` と互換性のある `2` × `2N` のサンプル配列で、形式は `[x_1, F(x_1), x_2, F(x_2), ...]` です。
