```
r = random_rotation_matrix() # 回転行列（直交座標系）
```

3x3のランダム回転行列`r`を生成します。この回転行列を使用して点`x`を`r * x`で回転させると、点`x`は半径`norm(x)`の球の表面上に一様にランダムに分布した位置に配置されます。ここで点`x`は直交座標系にあります。James Arvoの「Fast Random Rotation Matrices」を参照してください。

https://pdfs.semanticscholar.org/04f3/beeee1ce89b9adf17a6fabde1221a328dbad.pdf

# 戻り値

  * `r::Array{Float64, 2}`: 3x3のランダム回転行列
