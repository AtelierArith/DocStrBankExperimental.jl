```
cleared_img = clearborder(img)
cleared_img = clearborder(img, width)
cleared_img = clearborder(img, width, background)
```

画像の境界に接続されたオブジェクトをクリアした後の元の画像のコピーを返します。パラメータ：

  * img          = バイナリ/グレースケール入力画像
  * width        = 検査される境界の幅（デフォルト値は1）
  * background   = クリアされたピクセル/要素に与えられる値（デフォルト値は0）
