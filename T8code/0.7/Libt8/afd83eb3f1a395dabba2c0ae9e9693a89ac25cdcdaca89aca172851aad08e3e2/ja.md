```
t8_cmesh_get_attribute(cmesh, package_id, key, ltree_id)
```

ツリーの属性ポインタを返します。

!!! note
    *cmesh* はこの関数を呼び出す前にコミットされている必要があります。


# 引数

  * `cmesh`:[in] cmesh。
  * `package_id`:[in] 有効なソフトウェアパッケージの識別子。
  * `key`:[in] このツリーのすべての属性の中で同じ *package_id* を持つ属性を識別するために使用されるキー。
  * `tree_id`:[in] ツリーのローカル番号。

# 戻り値

ツリー *ltree_id* の属性ポインタ、または属性が見つからない場合は NULL。

# 参照

[`sc_package_register`](@ref), [`t8_cmesh_set_attribute`](@ref)

### プロトタイプ

```c
void * t8_cmesh_get_attribute (const t8_cmesh_t cmesh, const int package_id, const int key, const t8_locidx_t ltree_id);
```
