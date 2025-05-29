GaussianHermite{β}は、パラメータβを持つガウス・エルミートエンセmblesを表します。

Wigner{β}は同義語です。

使用例：

```
β = 2 #β = 1, 2, 4はそれぞれ実数、複素数、四元数行列を生成します。
d = Wigner{β} #GaussianHermite{β}と同じ

n = 20 #このサイズの正方行列を生成

S = rand(d, n)       #20x20の対称Wigner行列を生成
T = tridrand(d, n)   #対称三重対角形式を生成
v = eigvalrand(d, n) #固有値のサンプルを生成
```
