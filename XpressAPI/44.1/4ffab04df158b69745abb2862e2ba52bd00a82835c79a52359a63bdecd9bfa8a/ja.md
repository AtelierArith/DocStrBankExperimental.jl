```
XPRSdelcuts(prob, basis, cuttype, interp, delta, ncuts, cutind)::prob
```

現在のノードから行を削除します。

親ノードから自動的に復元された行は、XPRSaddcutsまたはXPRSloadcutsを使用して現在のノードに追加された行とともに削除される可能性があります。削除する行は、いくつかの方法で指定できます。いずれかの基準によって行が除外されると、それは削除されません。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `basis::Integer`: 1に設定すると基準が有効であることを保証します。
  * `cuttype::Integer`: 削除する行のユーザー定義タイプ。
  * `interp::Integer`: 行 `cuttype` の解釈方法: -1はすべての行タイプに一致; 1は行タイプを数値として扱う; 2は行タイプをビットマップとして扱う - `cuttype` に設定されたビットのいずれかが一致する場合に削除; 3は行タイプをビットマップとして扱う - `cuttype` に設定されたすべてのビットが一致する場合に削除。
  * `delta::Float64`: 絶対スラック値が `delta` より大きい行のみを削除します。
  * `ncuts::Integer`: 行のリストが提供された場合に削除する行の数。
  * `cutind::AbstractVector{Ptr{Cvoid}}`: 削除する行へのポインタを含む配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSdelcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelcuts.html) のドキュメントも参照してください。
