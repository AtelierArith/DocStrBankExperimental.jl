```
XPRSgetcpcutlist(prob, cuttype, interp, delta, maxcuts, cutind, viol)::ncuts, cutind, viol
```

カットプールからカットインデックスのリストを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `cuttype::Integer`: 返されるカットのユーザー定義タイプ。
  * `interp::Integer`: カットタイプの解釈方法: -1はすべてのカットを取得; 1はカットタイプを数値として扱う; 2はカットタイプをビットマップとして扱う - `cuttype`に設定されたビットのいずれかが一致する場合にカットを取得; 3はカットタイプをビットマップとして扱う - `cuttype`に設定されたすべてのビットが一致する場合にカットを取得。
  * `delta::Float64`: 有効な違反がデルタより大きいカットのみが返されます。
  * `maxcuts::Integer`: 返されるカットの最大数。
  * `cutind::Union{XPRSallocatable,Nothing,AbstractVector{Ptr{Cvoid}}}`: カットのポインタが返される`maxcuts`の長さの配列。適切なサイズの配列を関数に割り当てさせるためにこの引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `viol::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: カットの有効な違反の値が返される`maxcuts`の長さの倍精度配列。適切なサイズの配列を関数に割り当てさせるためにこの引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `ncuts::Int32`: カットプール内の`cuttype`タイプのカットの数が返される整数へのポインタ。
  * `cutind::Union{Nothing,AbstractVector{Ptr{Cvoid}}}`: カットのポインタが返される`maxcuts`の長さの配列。
  * `viol::Union{Nothing,AbstractVector{Float64}}`: カットの有効な違反の値が返される`maxcuts`の長さの倍精度配列。

C APIの対応する関数のドキュメント[XPRSgetcpcutlist](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcpcutlist.html)も参照してください。
