コールバック関数は、t8*forest*searchによって使用され、検索基準を説明します。要素に対して呼び出され、その要素で検索基準がチェックされるべきです。検索基準が満たされている場合はtrueを返し、そうでない場合はfalseを返します。

# 引数

  * `forest`:[in] 森
  * `ltreeid`:[in] 現在の木のローカルツリーID
  * `element`:[in] 検索基準がチェックされる要素
  * `is_leaf`:[in] *element* が葉要素である場合はtrue
  * `leaf_elements`:[in] *element* の子孫である*forest*内の葉要素（または*is_leaf*がtrueの場合は要素自体）
  * `tree_leaf_index`:[in] *leaf_elements*内の最初の葉のローカルインデックス

# 戻り値

検索基準が満たされている場合は非ゼロ、そうでない場合はゼロ。
