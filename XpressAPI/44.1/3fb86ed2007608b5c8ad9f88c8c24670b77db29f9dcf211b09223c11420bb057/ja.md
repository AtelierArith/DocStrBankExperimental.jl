```
XPRSaddcuts64(prob, ncuts, cuttype, rowtype, rhs, start, colind, cutcoef)::prob
```

現在のノードに直接カットを追加します。

カットは自動的にカットプールに追加されます。ノードに追加されたカットは、明示的にXPRSdelcutsを呼び出して削除しない限り、すべての子孫ノードに自動的に継承されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncuts::Integer`: 追加するカットの数。
  * `cuttype::AbstractVector{Integer}`: ユーザーが割り当てたカットタイプを含む長さ`ncuts`の整数配列。
  * `rowtype::AbstractVector{Cchar}`: 行タイプを含む長さ`ncuts`の文字配列：Lは`<=`行を示し、Gは`>=`行を示し、Eは`=`行を示します。
  * `rhs::AbstractVector{Number}`: カットの右辺要素を含む長さ`ncuts`の倍精度配列。
  * `start::AbstractVector{Integer}`: 各カットの開始を示す`colind`および`cutcoef`配列へのオフセットを含む整数配列。
  * `colind::AbstractVector{Integer}`: カット内の列インデックスを含む長さ`start[ncuts]`の整数配列。
  * `cutcoef::AbstractVector{Number}`: カットの行列値を含む長さ`start[ncuts]`の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSaddcuts64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddcuts64.html)のドキュメントも参照してください。
