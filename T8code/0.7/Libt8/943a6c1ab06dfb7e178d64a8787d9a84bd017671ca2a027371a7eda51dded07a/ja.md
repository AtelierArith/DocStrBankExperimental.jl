```
t8_element_transform_face(ts, elem1, elem2, orientation, sign, is_smaller_face)
```

2つの木が共通の面fを共有していると仮定します。1つの木のfの部分面である要素eと木の接続の向きが与えられた場合、eと論理的に一致するが隣接する木の座標系にある顔要素を構築します。

!!! note
    *elem1* と *elem2* は同じ要素を指す場合があります。


# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem1`:[in] 面要素。
  * `elem2`:[in,out] 戻り値として、他の木の座標系に関する面要素 *elem1*。
  * `orientation`:[in] 木-木接続の向き。
  * `sign`:[in] 2つの木の面のトポロジーの向きに応じて、0（両方の面が逆の向きを持つ）または1（両方の面が同じ上向きの向きを持つ）。 t8*eclass*face_orientation
  * `is_smaller_face`:[in] *elem1* が小さい面に属するかどうかを宣言するフラグ。木Tの面fは、木T'の面f'よりも小さい場合、Tのeclassが小さいか、クラスが等しくf<f'の場合です。向きは小さい面に関連して定義されます。

# 参照

[`t8_cmesh_set_join`](@ref)

### プロトタイプ

```c
void t8_element_transform_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, t8_element_t *elem2, int orientation, int sign, int is_smaller_face);
```
