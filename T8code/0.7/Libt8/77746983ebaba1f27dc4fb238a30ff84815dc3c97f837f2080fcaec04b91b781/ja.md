```
t8_cmesh_set_partition_uniform(cmesh, element_level, ts)
```

与えられたスキームのために、指定されたレベルの均一な細分化に従って派生cmeshを分割する必要があるかどうかを宣言します。この呼び出しは、cmeshがまだt8*cmesh*commitへの呼び出しを介してコミットされていない場合、かつcmeshが派生される場合にのみ有効です。

# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `element_level`:[in] 細分化レベル。
  * `ts`:[in] 細分化パターンを説明する要素スキーム。所有権を取得します。これは、この関数を呼び出す前に**ts**を参照することで防ぐことができます。

### プロトタイプ

```c
void t8_cmesh_set_partition_uniform (t8_cmesh_t cmesh, int element_level, t8_scheme_cxx_t *ts);
```
