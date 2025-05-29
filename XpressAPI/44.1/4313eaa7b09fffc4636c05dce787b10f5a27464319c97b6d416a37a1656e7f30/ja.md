```
XPRSdelcpcuts(prob, cuttype, interp, ncuts, cutind)::prob
```

分岐限定探索中に、カットは子ノードで適用されるためにカットプールに保存されます。

これらのカットは、XPRSdelcutsを使用して特定のノードから削除できますが、多くのケースでこれを適用する場合、カットをカットプールから完全に削除する方が望ましいかもしれません。これは`XPRSdelcpcuts`を使用して達成されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `cuttype::Integer`: 一致させるユーザー定義のカットタイプ。
  * `interp::Integer`: カット`cuttype`の解釈方法： -1はすべてのカットタイプに一致; 1はカットタイプを数値として扱う; 2はカットタイプをビットマップとして扱う - `cuttype`に設定されたビットのいずれかが一致する場合に削除; 3はカットタイプをビットマップとして扱う - `cuttype`に設定されたすべてのビットが一致する場合に削除。
  * `ncuts::Integer`: 削除するカットの数。
  * `cutind::AbstractVector{Ptr{Cvoid}}`: 削除するカットへのポインタを含む配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSdelcpcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelcpcuts.html)のドキュメントも参照してください。
