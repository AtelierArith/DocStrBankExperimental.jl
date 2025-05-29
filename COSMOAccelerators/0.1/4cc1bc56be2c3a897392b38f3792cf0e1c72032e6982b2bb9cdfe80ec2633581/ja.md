update!(aa, g, x, iter)

  * アクセラレータ `aa` の履歴を反復 g = g(xi) で更新します
  * 残差 f = x - g を計算します
  * ロギングのために反復 `iter` が渡されます
