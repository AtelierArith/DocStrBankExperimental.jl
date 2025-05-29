Truncate(ξ::Int)

ウィンドウの半サイズがξに等しい`Bartlett<:Smoother`を構築します。

行列A[i,j]の平滑化されたバージョンは次のように定義されます。

$$
A[t, j] = \frac{1}{S_T} \sum_{s=max{t-T,-ξ}}^{min{t-1, ξ}} (1-|s/S_T|) A[t-s,j]
$$

ここで、$S_T = (2\xi+1)/2$はバンド幅です。
