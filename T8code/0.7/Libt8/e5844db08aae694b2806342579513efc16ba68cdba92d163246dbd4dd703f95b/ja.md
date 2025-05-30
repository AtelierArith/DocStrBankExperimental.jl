```
t8_cmesh_tree_to_face_decode(dimension, tree_to_face, face, orientation)
```

与えられたツリーから面への値を使用して、そのエンコードされた面番号と向きを取得します。

!!! note
    この関数は t8*cmesh*tree*to*face*encode の逆操作です。F = t8*eclass*max*num*faces[dimension] の場合、orientation = tree*to*face / F face = tree*to_face % F となります。


# 引数

  * `dimension`:[in] 対応する eclass の次元。
  * `tree_to_face`:[in] ツリーから面への値
  * `face`:[out] 出力時に格納された面の値で埋められます。
  * `orientation`:[out] 出力時に格納された向きの値で埋められます。

### プロトタイプ

```c
void t8_cmesh_tree_to_face_decode (const int dimension, const int8_t tree_to_face, int *face, int *orientation);
```
