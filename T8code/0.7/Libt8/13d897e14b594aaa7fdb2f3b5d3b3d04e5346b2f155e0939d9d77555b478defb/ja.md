```
t8_cmesh_set_attribute(cmesh, gtree_id, package_id, key, data, data_size, data_persists)
```

cmeshのツリーに属性を格納します。属性はツリーに関連付けられた内部ストレージにコピーされる任意のデータです。各アプリケーションは複数の属性を設定でき、属性は整数キーによって区別されます。各アプリケーションは任意の整数をキーとして使用できます。

!!! note
    指定されたpackage_idとkeyを持つ属性がすでに存在する場合、それは上書きされます。


# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `gtree_id`:[in] ツリーのグローバルID。
  * `package_id`:[in] 有効なソフトウェアパッケージの一意の識別子。
  * `key`:[in] 同じpackage*idを持つすべての属性の下でこの属性を識別するために使用される整数キー。*key*はこのツリーとpackage*idに対して一意の値でなければなりません。
  * `data`:[in] 属性データへのポインタ。
  * `data_size`:[in] 属性のバイト数。
  * `data_persists`:[in] このフラグはメモリを最適化するために使用できます。trueの場合、t8codeはt8*cmesh*commitが呼び出されたときに*data*が指すメモリに属性データが存在すると仮定します（これはよりメモリ効率的です）。フラグがfalseの場合、データの内部コピーが即座に作成され、このコピーがコミット時に使用されます。いずれの場合も、[`t8_cmesh_commit`](@ref)の後にt8_codeによってデータのコピーが使用されます。

# 参照

[`sc_package_register`](@ref)

### プロトタイプ

```c
void t8_cmesh_set_attribute (t8_cmesh_t cmesh, t8_gloidx_t gtree_id, int package_id, int key, void *data, size_t data_size, int data_persists);
```
