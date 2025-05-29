```
t8_cmesh_register_geometry(cmesh, geometry)
```

cmeshにジオメトリを登録します。cmeshはジオメトリの所有権を持ちます。

ジオメトリが登録されておらず、cmeshが別のcmeshから変更された場合、他のcmeshのジオメトリが使用されます。

!!! note
    t8*cmesh*bcastを使用する必要がある場合、すべてのジオメトリはbcast操作の*後*に登録する必要があります。前ではありません。


# 引数

  * `cmesh`:[in,out] cmesh。
  * `geometry`:[in] 登録するジオメトリ。

### プロトタイプ

```c
void t8_cmesh_register_geometry (t8_cmesh_t cmesh, t8_geometry_c *geometry);
```
