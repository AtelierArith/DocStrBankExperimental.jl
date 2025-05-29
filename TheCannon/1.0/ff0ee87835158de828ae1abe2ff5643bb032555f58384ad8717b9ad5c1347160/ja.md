`theta`の二次項を対称行列として取得します。`nlabels x nlabels x npixels`の次元の配列を返します。

```
Q = quad_coeff_matrix(theta)
Q[:, :, 1] #最初のピクセルの二次係数
```
