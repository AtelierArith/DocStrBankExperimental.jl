コールバック関数のプロトタイプは、細分化と粗視化を決定するためのものです。*is_family* が 1 の場合、*elements* の最初の *num_elements* がファミリーを形成し、このファミリーを粗視化するか、最初の要素のみを細分化するかを決定します。そうでない場合、*is_family* は 0 でなければならず、細分化のために要素配列の最初のエントリを考慮します。最初の *num_elements* を超える要素配列のエントリは未定義です。

# 引数

  * `forest`:[in] 新しい要素が属するフォレスト
  * `forest_from`:[in] 適応されるフォレスト
  * `which_tree`:[in] *elements* を含むローカルツリー
  * `lelement_id`:[in] 現在の要素のツリー内の *forest_old* におけるローカル要素 ID
  * `ts`:[in] ツリーの eclass スキーム
  * `is_family`:[in] 1 の場合、*elements* の最初の *num_elements* エントリがファミリーを形成します。0 の場合、形成しません。
  * `num_elements`:[in] *elements* で定義されているエントリの数
  * `elements`:[in] ファミリーへのポインタ、または *is_family* が 0 の場合は 1 つの要素へのポインタ。

# 戻り値

*elements* の最初のエントリを細分化すべき場合は 1、ファミリー *elements* を粗視化すべき場合は -1、*elements* の最初のエントリを削除すべき場合は -2、その他の場合は 0 を返します。
