```
plot_tfbdry([plt], tree[; start, nd_col, ln_col, bg_col])
```

与えられたツリーに対して、葉ノードの視覚的表現を出力します。ユーザーは各レベルのノードカウントを0または1から開始するオプションがあります。

# 引数

  * `plt::Plots.Plot`: プロットオブジェクト。
  * `tree::BitVector`: 葉ノードをプロットするためのツリー。`BitVector`の形式で提供されます。
  * `depth::Integer`: (デフォルト: `log2(length(tree)+1)-1 |> Int`) 表示される最大深さ。

# キーワード引数

  * `start::Integer`: (デフォルト: `0`) ツリーのルートをゼロインデックスまたは1インデックスにするかどうか。
  * `node_color::Symbol`: (デフォルト: `:black`) 葉ノードの色。
  * `line_color::Symbol`: (デフォルト: `:black`) プロット内の線の色。
  * `background_color::Symbol`: (デフォルト: `:white`) 背景の色。

# 戻り値

`::Plots.Plot`: 葉ノードの視覚的表現を持つプロットオブジェクト。

# 例

```julia
using Wavelets, WaveletsExt

# Wavelets `maketree`を使用してツリーを構築
tree = maketree(128, 7, :dwt)

# 葉ノードをプロット
plot_tfbdry(tree)
```

**参照:** [`plot_tfbdry!`](@ref), [`plot_tfbdry2`](@ref)
