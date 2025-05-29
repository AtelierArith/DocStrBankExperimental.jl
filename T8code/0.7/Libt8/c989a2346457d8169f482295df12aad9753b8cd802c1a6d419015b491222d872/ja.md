解析幾何関数の定義。この関数は参照座標を物理座標にマッピングします。

```c++
 [0,1]^\mathrm{dim} 
```

.

# 引数

  * `cmesh`:[in] cmesh。
  * `gtreeid`:[in] 参照点が存在するcmeshのグローバルツリー。
  * `ref_coords`:[in] 次元 x *num_coords* のエントリを指定する配列、点を指定します。
  * `num_coords`:[in]
  * `out_coords`:[out] 物理空間における*ref_coords*のマッピングされた座標。長さは*num_coords* * 3です。
  * `tree_data`:[in] t8*geom*load*tree*data_fnによってロードされた現在のツリーのデータ。
  * `user_data`:[in] ジオメトリに格納されたユーザーデータポインタ。
