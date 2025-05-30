```
t8_element_face_child_face(ts, elem, face, face_child)
```

要素の面とその面の子の番号を与えると、その子の要素の面番号を返します。

```c++
  x ---- x   x      x           x ---- x
  |      |   |      |           |   |  | <-- f
  |      |   |      x           |   x--x
  |      |   |                  |      |
  x ---- x   x                  x ---- x
   elem    face  face_child    Returns the face number f
```

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 要素。
  * `face`:[in] 面の番号。
  * `face_child`:[in] 0 <= *face_child* < num*face*children の番号で、*face* と共有する *elem* の子を指定します。これらの子は線形順序で数えられます。これは、t8*element*children*at*face の呼び出しからの子の順序と一致します。

# 戻り値

*elem* の子の面で *face_child* と一致する面の番号を返します。

### プロトタイプ

```c
int t8_element_face_child_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, int face_child);
```
