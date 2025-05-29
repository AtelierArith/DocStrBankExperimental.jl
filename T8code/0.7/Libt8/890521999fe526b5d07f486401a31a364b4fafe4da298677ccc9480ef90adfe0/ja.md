```
t8_cmesh_set_attribute_string(cmesh, gtree_id, package_id, key, string)
```

cmeshのツリーに属性として文字列を保存します。

!!! note
    t8*cmesh*set_attributeを使用することもできますが、文字列用のこの特化した関数を使用することをお勧めします。


!!! note
    指定されたpackage_idとkeyを持つ属性がすでに存在する場合、それは上書きされます。


# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `gtree_id`:[in] ツリーのグローバルID。
  * `package_id`:[in] 有効なソフトウェアパッケージの一意の識別子。
  * `key`:[in] 同じpackage*idを持つすべての属性の下でこの属性を識別するために使用される整数キー。*key*はこのツリーとpackage*idに対して一意の値でなければなりません。
  * `string`:[in] 属性として保存する文字列。

# 参照

[`sc_package_register`](@ref)

### プロトタイプ

```c
void t8_cmesh_set_attribute_string (t8_cmesh_t cmesh, t8_gloidx_t gtree_id, int package_id, int key, const char *string);
```
