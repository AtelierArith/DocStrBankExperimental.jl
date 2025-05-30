```
plot_tfbdry2!([plt], tree, [n, m; line_color, background_color])
```

クワッドツリーを与えると、現在のプロットオブジェクト `plt` の上に葉ノードの視覚的表現を出力します。

# 引数

  * `plt::Plots.Plot`: プロットオブジェクト。
  * `tree::BitVector`: 葉ノードをプロットするためのツリー。`BitVector` の形式で提供されます。
  * `n::Integer`: 信号の垂直サイズ。
  * `m::Integer`: 信号の水平方向のサイズ。

# キーワード引数

  * `line_color::Symbol`: (デフォルト: `:black`) プロット内の線の色。
  * `background_color::Symbol`: (デフォルト: `:white`) 背景の色。

# 戻り値

`::Plots.Plot`: 葉ノードの視覚的表現を持つプロットオブジェクト。

# 例

```julia
using Wavelets, WaveletsExt

# Wavelets `maketree` を使用してクワッドツリーを構築
tree = maketree(128, 128, 7, :dwt)

# 葉ノードをプロット
plot_tfbdry2!(tree)
```

**参照:** [`plot_tfbdry2`](@ref), [`plot_tfbdry`](@ref)
