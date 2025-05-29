```
PLSENLPModel{G, T, S, M <: AbstractNLPModel{T, S}, Meta <: AbstractNLPModelMeta{T, S},} <: AbstractPQNNLPModel{T,S}
```

PLSEヘッセ行列近似を使用してNLPModelの分割構造を推定し割り当てます。`PLSENLPModel`には以下のフィールドがあります：

  * `model`: 元のモデル;
  * `meta`: `PLSENLPModel`に関する情報を収集;
  * `counters`: 呼び出された`NLPModels`の標準メソッドの数をカウント;
  * `n`: 問題のサイズ;
  * `N`: 要素関数の数;
  * `vec_elt_fun`: サイズ`N`の`ElementFunction`ベクター;
  * `M`: 異なる要素関数の表現木の数;
  * `vec_elt_complete_expr_tree`: サイズ`M`の`Complete_expr_tree`ベクター;
  * `element_expr_tree_table`: サイズ`M`のベクターで、i番目の要素`element_expr_tree_table[i]::Vector{Int}`は、どの要素関数が`vec_elt_complete_expr_tree[i]`の表現木を使用しているかを示します;
  * `index_element_tree`: サイズ`N`のベクターで、各コンポーネントは対応する要素に対して`vec_elt_complete_expr_tree`からどの`Complete_expr_tree`が使用されているかを示します;
  * `vec_compiled_element_gradients`: 各要素の勾配評価のためにコンパイルされたテープを集めるベクター;
  * `op`: 分割された行列（主メモリコスト）;
  * `name`: 実行された分割準ニュートン更新の名前;
