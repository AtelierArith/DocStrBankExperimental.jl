```
XPRSloadcuts(prob, cuttype, interp, ncuts, cutind)::prob
```

カットプールから行列にカットをロードします。

`XPRSloadcuts`を呼び出さない限り、カットはカットプールに残りますが、ノードではアクティブにはなりません。ノードでロードされたカットは、`XPRSdelcuts`を使用して削除されない限り、すべての子孫ノードでアクティブなままです。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `cuttype::Integer`: カットタイプ。
  * `interp::Integer`: カットタイプの解釈方法： -1はすべてのカットをロード; 1はカットタイプを数値として扱う; 2はカットタイプをビットマップとして扱う - `cuttype`に設定されたビットのいずれかと一致するビットがあればカットをロード; 3はカットタイプをビットマップとして扱う - `0`は`cuttype`に設定されたすべてのビットと一致する場合にカットをロード。
  * `ncuts::Integer`: ロードするカットの数。
  * `cutind::AbstractVector{Ptr{Cvoid}}`: 行列にロードするカットへのポインタを含む長さ`ncuts`の配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSloadcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadcuts.html)のドキュメントも参照してください。
