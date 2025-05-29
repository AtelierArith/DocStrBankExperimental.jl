コールバック関数プロトタイプは、クアドラントのユーザーデータを初期化します。

### パラメータ

  * `p4est`:[in] 森
  * `which_tree`:[in] *クアドラント*を含む木
  * `quadrant`:[in,out] 初期化されるクアドラント: data_size > 0 の場合、初期化されるデータは *quadrant*->p.user*data; そうでない場合、ポインタでないユーザーデータ（例えば *quadrant*->p.user*int）は初期化できます
