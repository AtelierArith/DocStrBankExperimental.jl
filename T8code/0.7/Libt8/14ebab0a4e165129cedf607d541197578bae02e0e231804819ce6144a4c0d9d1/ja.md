```
t8_cmesh_set_attribute_gloidx_array(cmesh, gtree_id, package_id, key, data, data_count, data_persists)
```

[`t8_gloidx_t`](@ref) の配列を cmesh のツリーに属性として保存します。

!!! note
    t8*cmesh*set_attribute を使用することもできますが、配列用のこの専門的な関数を使用することをお勧めします。


!!! note
    指定された package_id と key の属性がすでに存在する場合、それは上書きされます。


!!! note
    属性配列のデータエントリ数 *data_count* は保存しません。別の属性を使用してデータカウントを自分で追跡できます。


# 引数

  * `cmesh`:[in,out] 更新される cmesh。
  * `gtree_id`:[in] ツリーのグローバル ID。
  * `package_id`:[in] 有効なソフトウェアパッケージの一意の識別子。
  * `key`:[in] 同じ package*id のすべての属性の下でこの属性を識別するために使用される整数キー。*key* はこのツリーと package*id に対して一意の値でなければなりません。
  * `data`:[in] 属性として保存する配列。
  * `data_count`:[in] *data* のエントリ数。
  * `data_persists`:[in] このフラグはメモリを最適化するために使用できます。true の場合、t8code は t8*cmesh*commit が呼び出されたときに *data* が指すメモリに属性データが存在すると仮定します（これはよりメモリ効率が良いです）。フラグが false の場合、データの内部コピーが即座に作成され、このコピーがコミット時に使用されます。いずれの場合も、[`t8_cmesh_commit`](@ref) の後に t8_code によってデータのコピーが使用されます。

# 参照

[`sc_package_register`](@ref)

### プロトタイプ

```c
void t8_cmesh_set_attribute_gloidx_array (t8_cmesh_t cmesh, t8_gloidx_t gtree_id, int package_id, int key, const t8_gloidx_t *data, const size_t data_count, int data_persists);
```
