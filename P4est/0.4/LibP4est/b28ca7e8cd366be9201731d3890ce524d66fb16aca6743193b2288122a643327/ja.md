```
p4est_refine(p4est_, refine_recursive, refine_fn, init_fn)
```

フォレストを洗練します。

### パラメータ

  * `p4est`:[in,out] フォレストはその場で変更されます。
  * `refine_recursive`:[in] 再帰的な洗練を決定するためのブール値。
  * `refine_fn`:[in] 四分木を洗練する必要がある場合にtrueを返すコールバック関数。refine*recursiveがtrueの場合、refine*fnは既存の四分木と新しく作成された四分木のすべてに対して呼び出されます。そうでない場合は、既存の四分木に対してのみ呼び出されます。コールバックによって行われた洗練要求が無視される可能性があります。この場合をキャッチするために、init*fnが呼び出されるかどうかを調べるか、`p4est*refine*ext`[@ref]をp4est*extended.hで使用し、replace_fnが呼び出されるかどうかを調べることができます。
  * `init_fn`:[in] 新しく作成された四分木のuser_dataを初期化するためのコールバック関数で、すでに割り当てられています。この関数ポインタはNULLである可能性があります。

### プロトタイプ

```c
void p4est_refine (p4est_t * p4est, int refine_recursive, p4est_refine_t refine_fn, p4est_init_t init_fn);
```
