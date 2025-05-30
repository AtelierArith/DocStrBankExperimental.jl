```
t8_cmesh_get_attribute_gloidx_array(cmesh, package_id, key, ltree_id, data_count)
```

木の gloidx_t 配列の属性ポインタを返します。

!!! note
    *cmesh* はこの関数を呼び出す前にコミットされている必要があります。


!!! note
    属性配列のデータエントリの数を保存していないため、実際に *data_count* の数のエントリが保存されているかどうかのチェックは行われません。別の属性を使用してデータカウントを自分で追跡することができます。


# 引数

  * `cmesh`:[in] cmesh。
  * `package_id`:[in] 有効なソフトウェアパッケージの識別子。
  * `key`:[in] 同じ *package_id* を持つこの木のすべての属性の下で属性を識別するために使用されるキー。
  * `ltree_id`:[in] 木のローカル番号。
  * `data_count`:[in] 要求される配列のエントリ数。この数は、対応する t8*cmesh*set*attribute*gloidx*array への呼び出しの *data*count* パラメータ以下でなければなりません。

# 戻り値

木 *ltree_id* の属性ポインタ、または属性が見つからない場合は NULL。

# 参照

[`sc_package_register`](@ref), [`t8_cmesh_set_attribute_gloidx_array`](@ref)

### プロトタイプ

```c
t8_gloidx_t * t8_cmesh_get_attribute_gloidx_array (const t8_cmesh_t cmesh, const int package_id, const int key, const t8_locidx_t ltree_id, const size_t data_count);
```
