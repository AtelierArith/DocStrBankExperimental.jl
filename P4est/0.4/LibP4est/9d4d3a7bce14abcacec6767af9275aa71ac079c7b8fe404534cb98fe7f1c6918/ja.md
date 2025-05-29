```
p4est_connectivity_new_twotrees(l_face, r_face, orientation)
```

ユーザー定義の方法で互いに回転している2つの木の接続構造を作成します

### パラメータ

  * `l_face`:[in] 左の面のインデックス
  * `r_face`:[in] 右の面のインデックス
  * `orientation`:[in] 木の相互の向き

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_new_twotrees (int l_face, int r_face, int orientation);
```
