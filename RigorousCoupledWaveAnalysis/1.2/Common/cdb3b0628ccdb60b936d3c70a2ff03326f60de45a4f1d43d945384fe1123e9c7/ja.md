```
recip2real(dnx,dny,F)
recip2real(dnx,dny,F,sx,sy)
```

逆空間畳み込み行列を2D実空間パターンに変換します。sxとsyを指定することで画像の解像度を上げることができます。指定しない場合は、直接fftが実行され、結果は逆空間表現と同じサイズになります。

# 引数

  * `dnx` : x方向の逆空間グリッド
  * `dny` : y方向の逆空間グリッド
  * `F`: 逆空間畳み込み行列
  * `sx`: x軸に沿った結果のピクセル数
  * `sy`: y軸に沿った結果のピクセル数

# 出力

  * `f` : Fに対応するバイナリ実空間表現
