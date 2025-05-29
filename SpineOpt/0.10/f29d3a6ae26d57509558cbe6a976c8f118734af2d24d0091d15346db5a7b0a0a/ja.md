```
prepare_spineopt(url_in; <keyword arguments>)
```

`url_in`の内容からSpineOptモデルを作成します - [run_spineopt!](@ref)に渡す準備が整いました。引数`url_in`は、有効なSpineデータベースを指す`String`であるか、手動で作成されたかjsonファイルから解析された`Dict`でなければなりません。

# 引数

  * `log_level`
  * `upgrade`
  * `filters`
  * `templates`
  * `mip_solver`
  * `lp_solver`
  * `use_direct_model`
  * `use_model_names`
  * `add_bridges`

キーワード引数の説明については[run_spineopt](@ref)を参照してください。
