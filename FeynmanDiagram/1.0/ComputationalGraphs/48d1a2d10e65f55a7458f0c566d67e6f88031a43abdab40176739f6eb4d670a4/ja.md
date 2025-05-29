```
function linear_combination(graphs::Vector{Graph{F,W}}, constants::AbstractVector=ones(F, length(graphs))) where {F,W}
```

グラフのベクトル 𝐠 と同じサイズの定数のベクトル 𝐜 を与えると、線形結合 (𝐜 ⋅ 𝐠) を表す新しいグラフを返します。この関数は、入力 `graphs` からユニークなグラフを特定し、それに関連する `constants` を合計します。すべての入力グラフは同じ次数でなければなりません。

# 引数:

  * `graphs`  計算グラフのベクトル
  * `constants`  スカラー倍のベクトル (デフォルトは ones(F, length(graphs)))。

# 戻り値:

  * ユニークな入力 `graphs` の線形結合を定数で重み付けした新しい `Graph{F,W}` オブジェクト、

入力 `graphs` の重複グラフは、それに関連する定数を合計することによって結合されます。

# 例:

```
グラフ `g1`、`g2`、`g1` と定数 `c1`、`c2`、`c3` が与えられた場合、関数は `(c1+c3)*g1 + c2*g2` を計算します。
```
