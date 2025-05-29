```
t8_cmesh_set_join(cmesh, gtree1, gtree2, face1, face2, orientation)
```

2つのツリー間にフェイス接続を挿入します。

# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `tree1`:[in] 2つのツリーのうち最初のツリーのツリーID。
  * `tree2`:[in] 2つのツリーのうち2番目のツリーのツリーID。
  * `face1`:[in] 最初のツリーのフェイス番号。
  * `face2`:[in] 2番目のツリーのフェイス番号。
  * `orientation`:[in] face1とface2が互いにどのように向いているかを指定します TODO: orientationはすべての要素クラスに対して慎重に定義する必要があります。TODO: orientationを文書化する

### プロトタイプ

```c
void t8_cmesh_set_join (t8_cmesh_t cmesh, t8_gloidx_t gtree1, t8_gloidx_t gtree2, int face1, int face2, int orientation);
```
