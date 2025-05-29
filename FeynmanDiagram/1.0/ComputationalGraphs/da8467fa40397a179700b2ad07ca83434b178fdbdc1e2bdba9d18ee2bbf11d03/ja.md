```
function linear_combination(graphs::Vector{FeynmanGraph{F,W}}, constants::AbstractVector=ones(F, length(graphs))) where {F,W}
```

同じタイプと外部/内部頂点を持つグラフのベクトル 𝐠 と、同じサイズの定数のベクトル 𝐜 を与えると、線形結合 (𝐜 ⋅ 𝐠) を表す新しいグラフを返します。この関数は、入力 `graphs` からユニークなグラフを特定し、それに関連付けられた `constants` を合計します。すべての入力グラフは、同じ図のタイプ、次数、および外部頂点を持っている必要があります。

# 引数:

  * `graphs`  入力FeynmanGraphsのベクトル
  * `constants`  スカラー倍のベクトル（デフォルトは ones(F, length(graphs))）。

# 戻り値:

  * 定数によって重み付けされたユニークな入力 `graphs` の線形結合を表す新しい `FeynmanGraph{F,W}` オブジェクト、

入力 `graphs` の重複グラフは、それに関連付けられた定数を合計することによって結合されます。

# 例:

```
グラフ `g1`、`g2`、`g1` と定数 `c1`、`c2`、`c3` が与えられた場合、関数は `(c1+c3)*g1 + c2*g2` を計算します。
```
