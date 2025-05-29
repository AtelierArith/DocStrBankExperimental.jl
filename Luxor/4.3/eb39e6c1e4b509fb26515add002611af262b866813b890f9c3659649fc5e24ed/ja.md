```
noise(x)          ; detail = 1, persistence = 1.0) # 1D
noise(x, y)       ; detail = 1, persistence = 1.0) # 2D
noise(x, y, z)    ; detail = 1, persistence = 1.0) # 3D
noise(x, y, z, w) ; detail = 1, persistence = 1.0) # 4D
```

`x`、`y`、`z`、および `w` の値に対応する 0.0 から 1.0 の間のノイズ値を生成します。単独の `x` 値は 1D ノイズを生成し、`x` と `y` は 2D ノイズを生成し、以降同様です。

`detail` 値は整数（>= 1）で、生成したいノイズのオクターブ数を指定します。

`persistence` 値は通常 0.0 から 1.0 の間で、`detail` が 1 より大きい場合に各連続オクターブの振幅がどれだけ早く減少するかを制御します。
