コールバック関数は、t8*forest*searchによるクエリに使用されます。要素に対して呼び出され、その要素に対してすべてのクエリがチェックされます。すべての正のクエリは、要素の子にさらに渡され、ツリーの葉要素まで進みます。チェックの結果は*query_matches*に格納されます。

# 引数

  * `forest`:[in] 森
  * `ltreeid`:[in] 現在のツリーのローカルツリーID
  * `element`:[in] クエリが実行される要素
  * `is_leaf`:[in] *element*が葉要素である場合のみtrue
  * `leaf_elements`:[in] *element*の子孫である*forest*内の葉要素（または*is_leaf*がtrueの場合は要素自体）
  * `tree_leaf_index`:[in] *leaf_elements*内の最初の葉のローカルインデックス
  * `queries`:[in] 関数によってチェックされるクエリの配列
  * `query_indices`:[in] 各エントリがqueries内のクエリのインデックスであるsize_tエントリの配列。
  * `query_matches`:[in,out] 長さ*num*active*queries*の配列。要素が葉でない場合、i番目のインデックスでtrueまたはfalseに設定する必要があります。これは、要素がi番目のクエリインデックスのクエリに「一致」するかどうかを指定します。要素が葉である場合、すべてのエントリが設定される前に戻ることができます。
  * `num_active_queries`:[in] 現在アクティブなクエリの数（*query_matches*のエントリ数および*query_indices*のエントリ数に等しい）。
