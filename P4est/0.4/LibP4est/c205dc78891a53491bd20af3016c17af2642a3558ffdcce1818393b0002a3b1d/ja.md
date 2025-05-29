コールバック関数プロトタイプは、四分木のユーザーデータを初期化します。

### パラメータ

  * `p8est`:[in] 森
  * `which_tree`:[in] *quadrant*を含む木
  * `quadrant`:[in,out] 初期化される四分木: data_size > 0 の場合、初期化されるデータは *quadrant*->p.user*data にあります; そうでない場合、ポインタでないユーザーデータ（例えば *quadrant*->p.user*int）は初期化できます
