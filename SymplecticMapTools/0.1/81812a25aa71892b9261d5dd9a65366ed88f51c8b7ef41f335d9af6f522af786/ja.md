```
rectangular_window_weight(xs::AbstractArray, xlims::AbstractVector,
                          ylims::AbstractVector, α::Number)
```

`kernel_eigs` と `kernel_bvp` のためのシンプルな境界重み付け関数。`xlims` × `ylims` の外側でおおよそ 1、内側で 0 の重みをロジスティック関数の関数を介して返します。

引数:

  * `xs`: `d` × `N` の点の配列で、`d` は位相空間のサイズ、`N` は点の数です。
  * `xlims` と `ylims`: 重みがおおよそ 0 になる長方形を与える 2 ベクトル
  * `α`: ロジスティック関数の長さスケール（通常はドメインのサイズに対して小さい）

出力:

  * `w`: ウィンドウ重みを持つ `N` ベクトル
