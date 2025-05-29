`get_scc(fst::WFST, i = get_initial(fst;single=true); filter=arc->true)`

Tarjanのアルゴリズムを使用して、'fst'の強連結成分を計算します。タプル `(scc,c,v)` を返します：

  * `scc` は `fst` の強連結成分です
  * `c` は `i` からの到達可能性を含むブール配列です
  * `v` は `fst` の訪問済み状態です

関数 `filter` は、特定のプロパティを持つアークのみを考慮するために使用できます。
