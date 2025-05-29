```
t8_stash_add_attribute(stash, id, package_id, key, size, attr, copy)
```

ツリーに属性を追加します。

# 引数

  * `stash`:[in] 修正されるスタッシュ構造体。
  * `id`:[in] 属性が追加されるツリーのグローバルインデックス。
  * `package_id`:[in] 現在のパッケージのユニークID。
  * `key`:[in] この属性を識別するために使用される整数値。
  * `size`:[in] 属性のサイズ（バイト単位）。
  * `attr`:[in] 属性として保存されるべき*size*バイトのメモリを指します。
  * `copy`:[in] trueの場合、属性データは*attr*から内部ストレージにコピーされます。falseの場合、ポインタ*attr*のみが保存され、データはcmeshがコミットされるまでコピーされません。（よりメモリ効率が良いです）。

### プロトタイプ

```c
void t8_stash_add_attribute (t8_stash_t stash, t8_gloidx_t id, int package_id, int key, size_t size, void *const attr, int copy);
```
