```
t8_stash_class_bsearch(stash, tree_id)
```

クラススタッシュ内で指定されたツリーインデックスを持つエントリを検索します。スタッシュは事前にソートされている必要があります。

# 引数

  * `stash`:[in] 検索対象のスタッシュ。
  * `tree_id`:[in] グローバルツリーID。

# 戻り値

*tree_id*に対応する*stash*のクラス配列内の要素のインデックス。見つからない場合は-1。

### プロトタイプ

```c
ssize_t t8_stash_class_bsearch (t8_stash_t stash, t8_gloidx_t tree_id);
```
