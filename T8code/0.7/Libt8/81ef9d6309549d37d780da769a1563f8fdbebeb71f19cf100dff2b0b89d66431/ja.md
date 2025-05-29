コールバック関数は、クエリのために t8*forest*search によって使用されます。要素に対して呼び出され、その要素に対してすべてのクエリがチェックされます。すべての正のクエリは、要素の子にさらに渡され、木の葉要素まで続きます。チェックの結果は *query_matches* に格納されます。

# 引数

  * `forest`:[in] 森
  * `ltreeid`:[in] 現在の木のローカルツリーID
  * `element`:[in] クエリが実行される要素
  * `is_leaf`:[in] *element* が葉要素である場合にのみ true
  * `leaf_elements`:[in] *element* の子孫である *forest* の葉要素（または *is_leaf* が true の場合は要素自体）
  * `tree_leaf_index`:[in] *leaf_elements* の最初の葉のローカルインデックス
  * `queries`:[in] 関数によってチェックされるクエリの配列
  * `query_indices`:[in] 各エントリがクエリのインデックスである size_t エントリの配列。
  * `query_matches`:[in,out] 長さ *num*active*queries* の配列。要素が葉でない場合、各クエリの i 番目のインデックスで要素がクエリに「一致する」かどうかを指定するために、true または false に設定する必要があります。要素が葉である場合、すべてのエントリが設定される前に戻ることができます。
  * `num_active_queries`:[in] 現在アクティブなクエリの数（*query_matches* のエントリ数および *query_indices* のエントリ数に等しい）。
