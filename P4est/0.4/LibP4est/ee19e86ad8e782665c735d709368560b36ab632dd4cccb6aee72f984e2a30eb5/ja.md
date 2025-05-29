```
p8est_find_partition(num_procs, search_in, my_begin, my_end, _begin, _end)
```

パーティション配列における二分探索。二つのターゲット *my_begin* と *my_end* が与えられたとき、`search\_in[begin] >= my\_begin` かつ `my\_end <= search\_in[end]` となるオフセットを見つけます。条件を満たすインデックスが複数ある場合、最小のインデックスが結果となります。条件を満たすインデックスがない場合、*begin* と *end* を等しく設定しようとし、`search\_in[begin] >= my\_end` となるようにします。*my_begin* が *search_in* の最小値以下であれば、*begin* は 0 に設定され、*my_end* が *search_in* の最大値以上であれば、*end* は *num_procs* - 1 に設定されます。上記の条件のいずれも満たされない場合、出力は明確ではありません。`my_begin <= my_begin` を要求します。

### パラメータ

  * `num_procs`:[in] *search_in* の長さを取得するためのプロセス数。
  * `search_in`:[in] 関数が検索するソートされた配列（昇順）。`k` が search*in のインデックスである場合、`0 <= k < num\*procs` です。
  * `my_begin`:[in] 検索ウィンドウの開始を定義する最初のターゲット。
  * `my_end`:[in] 検索ウィンドウの終了を定義する二番目のターゲット。
  * `begin`:[in,out] `search\_in[begin] >= my\_begin` となる最初のオフセット。
  * `end`:[in,out] `my\_end <= search\_in[end]` となる二番目のオフセット。

### プロトタイプ

```c
void p8est_find_partition (const int num_procs, p4est_gloidx_t * search_in, p4est_gloidx_t my_begin, p4est_gloidx_t my_end, p4est_gloidx_t * begin, p4est_gloidx_t * end);
```
