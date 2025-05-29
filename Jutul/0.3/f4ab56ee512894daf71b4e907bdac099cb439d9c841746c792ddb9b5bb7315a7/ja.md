```
get_ad_entity_scalar(v::Real, npartials, diag_pos = nothing; <keyword_arguments>)
```

スカラーを取得し、部分導関数をADインスタンスとして取得します。

# 引数

  * `v::Real`: AD変数の値。
  * `npartials`: 各ADインスタンスが保持する部分導関数の数。
  * `diag_pos` = nothing: 0の代わりに部分導関数として1を設定する位置。

# キーワード引数

  * `tag = nothing`: ADインスタンスのタグ。異なるタグの2つのAD値は、摂動の混乱を避けるために相互作用できません（ForwardDiffのドキュメントを参照）。
