```julia
BahremanDarijani()
BahremanDarijani(type)

```

# モデル:

$$
W = \sum\limits_{i = 1}{3}\sum\limits_{j=0}^{N} A_j (\lambda_i^{m_j}-1) + B_j(\lambda_i^{-n_j}-1)
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか

# パラメータ:

  * `A2`
  * `B2`
  * `A4`
  * `A6`

> Bahreman M, Darijani H. 新しい多項式応力エネルギー関数; 有限伸長およびねじれ下のゴム状円筒への応用。応用ポリマー科学ジャーナル。2015年4月5日;132(13)。

