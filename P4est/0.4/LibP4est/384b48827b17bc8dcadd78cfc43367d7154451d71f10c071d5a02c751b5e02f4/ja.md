```
p6est_refine_columns(p6est_, refine_recursive, refine_fn, init_fn)
```

シートの列を洗練します。

### パラメータ

  * `p6est`:[in,out] フォレストはその場で変更されます。
  * `refine_recursive`:[in] 再帰的な洗練を決定するためのブール値。
  * `refine_fn`:[in] 列をより小さな列に洗練する必要がある場合にtrueを返さなければならないコールバック関数。refine*recursiveがtrueの場合、refine*fnは既存のすべての列と新しく作成された列に対して呼び出されます。そうでない場合は、既存の列に対してのみ呼び出されます。コールバックによって行われた洗練要求が無視される可能性があります。この場合をキャッチするために、init*fnが呼び出されるかどうかを調べるか、`p6est*refine*columns*ext`(@ref)をp6est*extended.hで使用し、replace*fnが呼び出されるかどうかを調べることができます。
  * `init_fn`:[in] すでに割り当てられた列内の新しく作成されたレイヤーのuser_dataを初期化するためのコールバック関数。この関数ポインタはNULLである可能性があります。

### プロトタイプ

```c
void p6est_refine_columns (p6est_t * p6est, int refine_recursive, p6est_refine_column_t refine_fn, p6est_init_t init_fn);
```
