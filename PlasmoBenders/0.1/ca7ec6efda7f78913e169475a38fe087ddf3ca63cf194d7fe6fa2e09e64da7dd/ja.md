```
BendersAlgorithm
```

グラフを用いた双対動的プログラミングのためのオプティマイザーオブジェクト。現在、線形ツリー構造にのみ実装されています。

属性には以下が含まれます（辞書として示されている場合、これはBendersサブプロブレムから記述されたデータへのマッピングです）

  * `graph` - Bendersを適用するためのPlasmo OptiGraph
  * `root_object` - Bendersアルゴリズムを開始する場所を示す`graph`内のノードまたはサブグラフ
  * `is_MIP` = 問題がMIPかどうかを示すブール値
  * `solve_order` - Bendersによって解決される順序のOptiNodesのベクトル
  * `solve_order_dict` - 特定のオブジェクトに対するすべての「次のオブジェクト」のベクトルへのマッピングを持つ辞書
  * `parent_objects` - 前のサブプロブレムへのマッピングを持つ辞書
  * `max_iters` - Bendersの最大反復回数
  * `time_limit` - Bendersを実行するために許可される最大時間（秒）
  * `tol` - 上限と下限の間の（絶対的）終了許容誤差
  * `current_iter` - Bendersアルゴリズムの現在の反復
  * `M` - 各反復におけるコスト・トゥ・ゴー関数の下限
  * `dual_iters` - 各反復における対応する双対値へのoptinodesのマッピングを持つ辞書；双対値は次のノードの解から得られます
  * `primal_iters` - 特定のノード上の複雑な変数の原始解へのoptinodesのマッピングを持つ辞書
  * `phis` - 直後のノードの目的関数へのoptinodesのマッピングを持つ辞書
  * `phis_LR` - 次のノードのラグランジアン（強化カットに使用）緩和の目的関数へのoptinodesのマッピングを持つ辞書；MIPsにおける強化Bendersカットに使用
  * `time_forward_pass` - フォワードパスに費やした時間（秒）
  * `time_backward_pass` - バックワードパスに費やした時間（秒）
  * `time_init` - オプティマイザーの初期化にかかる時間（秒）
  * `time_iterations` - 各反復に費やした時間のベクトル
  * `comp_vars` - ノードをその複雑な変数のベクトルにマッピングする辞書
  * `comp_var_map` - ノードを`comp_vars`内のインデックスにマッピングされた複雑な変数の辞書にマッピングする辞書
  * `var_copy_map` - ノードを次のノード上の複雑な変数のコピーにマッピングする辞書
  * `objective_value` - 最終目的値（上限から）
  * `lower_bounds` - 各反復における下限のベクトル
  * `upper_bounds` - 各反復における上限のベクトル
  * `regularize_data` - 正則化データオブジェクト
  * `binary_map` - ノードをそのノード上のバイナリ変数のベクトルにマッピングする辞書
  * `integer_map` - ノードをそのノード上の整数変数のベクトルにマッピングする辞書
  * `last_solutions` - ノードを最後の解のベクトルにマッピングする辞書
  * `var_solution_map` - 変数を`last_solutions`ベクトル上のインデックスにマッピングする辞書
  * `var_to_graph_map` - 変数をその所有するサブプロブレムサブグラフにマッピングする辞書
  * `feasibility_map` - 問題が実行可能であったかどうかの`solve_order`に一致する辞書
  * `options` - Bendersアルゴリズムのソルバーオプション
  * `ext` - 特定の手続きを拡張するための辞書
