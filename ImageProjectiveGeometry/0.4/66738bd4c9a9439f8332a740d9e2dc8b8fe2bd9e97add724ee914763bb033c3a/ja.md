structuretensor - 画像上で構造テンソル値を計算する

```
Usage:  (Ix2, Iy2, Ixy) = structuretensor(img, sigma=1)

Arguments: 
           img   - 処理する画像  ::Array{T,2}
           sigma - ガウス合計ウィンドウの標準偏差。使用する典型的な値は1-3です。デフォルトは1です。
Returns:
           Ix2   - x方向の勾配の2次モーメント
           Iy2   - y方向の勾配の2次モーメント
           Ixy   - xy方向の勾配の2次モーメント
```

See also: shi_tomasi(), harris(), noble(), coherence(), derivative5()
