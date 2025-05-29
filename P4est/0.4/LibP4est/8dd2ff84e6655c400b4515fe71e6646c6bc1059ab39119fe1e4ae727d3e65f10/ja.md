```
p6est_refine_columns_ext(p6est_, refine_recursive, maxlevel, refine_fn, init_fn, replace_fn)
```

境界のある細分化レベルと置換オプションを持つ森を水平方向に細分化します。

### パラメータ

  * `p6est`:[in,out] 森はその場で変更されます。
  * `refine_recursive`:[in] 再帰的な細分化を決定するためのブール値。
  * `maxlevel`:[in] 許可される最大細分化レベル（含む）。これが負の場合、レベルは `p4est.h` のコンパイル時定数 QMAXLEVEL のみで制限されます。
  * `refine_fn`:[in] 四分木を細分化する必要がある場合に true を返すコールバック関数。refine*recursive が true の場合、refine*fn は既存の四分木と新しく作成された四分木のすべてに対して呼び出されます。そうでない場合は、既存の四分木に対してのみ呼び出されます。コールバックによって行われた細分化要求が無視される可能性があります。この場合をキャッチするために、init*fn または replace*fn が呼び出されるかどうかを調べることができます。
  * `init_fn`:[in] 新しく作成された四分木の user_data を初期化するためのコールバック関数で、確実に割り当てられます。この関数ポインタは NULL である可能性があります。
  * `replace_fn`:[in] ユーザーが置き換える四分木に基づいて受信する四分木を変更できるようにするコールバック関数; NULL である可能性があります。

### プロトタイプ

```c
void p6est_refine_columns_ext (p6est_t * p6est, int refine_recursive, int maxlevel, p6est_refine_column_t refine_fn, p6est_init_t init_fn, p6est_replace_t replace_fn);
```
