解析幾何関数のヤコビアンの定義。

```c++
 [0,1]^\mathrm{dim} 
```

。

```c++
 \mathrm{dim} 
```

をマッピングします。

```c++
 \mathrm{dim} \cdot 3 
```

x *num_coords*。インデックス

```c++
 3 \cdot i
```

、

```c++
 3 \cdot i+1 
```

、

```c++
 3 \cdot i+2 
```

はヤコビアンの

```c++
 i 
```

列に対応します（エントリ

```c++
 3 \cdot i + j 
```

は

```c++
 \frac{\partial f_j}{\partial x_i} 
```

です）。

# 引数

  * `cmesh`:[in] cmesh。
  * `gtreeid`:[in] 参照点があるcmeshのグローバルツリー。
  * `ref_coords`:[in] ツリー次元 x *num_coords* の多くのエントリを持つ配列、ポイントを指定します。
  * `num_coords`:[in] ポイントの量。
  * `jacobian`:[out] *ref_coords* でのヤコビアン。サイズの配列。
  * `tree_data`:[in] t8*geom*load*tree*data_fn によってロードされた現在のツリーのデータ。
  * `user_data`:[in] 幾何学に格納されたユーザーデータポインタ。
