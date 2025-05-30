```
t8_forest_cmesh_ltreeid_to_ltreeid(forest, lctreeid)
```

森林の粗いメッシュ内の木のローカルIDを与えられた場合、その木の森林内のローカルIDを計算します。

!!! note
    森のローカルツリーに対して、これは t8*forest*ltreeid*to*cmesh_ltreeid の逆関数です。


# 引数

  * `forest`:[in] 森。
  * `ltreeid`:[in] *forest* の粗いメッシュ内の木のローカルID。

# 戻り値

森林内の木のローカルID。木が森林ローカルでない場合は -1 を返します。*forest* はこの関数を呼び出す前にコミットされている必要があります。

# 参照

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing 木のインデックス付けに関する詳細については、こちらをご覧ください。

### プロトタイプ

```c
t8_locidx_t t8_forest_cmesh_ltreeid_to_ltreeid (t8_forest_t forest, t8_locidx_t lctreeid);
```
