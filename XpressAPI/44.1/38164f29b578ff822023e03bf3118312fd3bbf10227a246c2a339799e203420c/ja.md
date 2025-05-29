```
XPRSstorecuts64(prob, ncuts, nodups, cuttype, rowtype, rhs, start, cutind, colind, cutcoef)::cutind
```

カットをカットプールに保存しますが、現在のノードには適用しません。

これらのカットは、アクティブになる前にXPRSloadcutsを使用して行列に明示的にロードする必要があります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncuts::Integer`: 追加するカットの数。
  * `nodups::Integer`: 0はカットプールから重複を除外しない; 1はカットプールから重複を除外する; 2はカットタイプを無視してカットプールから重複を除外する。
  * `cuttype::AbstractVector{Integer}`: カットタイプを含む長さ`ncuts`の整数配列。
  * `rowtype::AbstractVector{Cchar}`: 行タイプを含む長さ`ncuts`の文字配列: Lは`<=`行を示す; Eは=行を示す; Gは`>=`行を示す。
  * `rhs::AbstractVector{Number}`: カットの右辺要素を含む長さ`ncuts`の倍精度配列。
  * `start::AbstractVector{Integer}`: 各カットの開始を示す`colind`および`dmtval`配列へのオフセットを含む整数配列。
  * `cutind::Union{XPRSallocatable,AbstractVector{Ptr{Cvoid}}}`: カットへのポインタが返される長さ`ncuts`の配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てることができます。
  * `colind::AbstractVector{Integer}`: カット内の列インデックスを含む長さ`start[ncuts]`の整数配列。
  * `cutcoef::AbstractVector{Number}`: カットの行列値を含む長さ`start[ncuts]`の倍精度配列。

# 戻り値

  * `cutind::AbstractVector{Ptr{Cvoid}}`: カットへのポインタが返される長さ`ncuts`の配列。

C APIの対応する関数[XPRSstorecuts64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSstorecuts64.html)のドキュメントも参照してください。
