Truncate(ξ::Int)

ウィンドウの半サイズがξに等しい`Truncated<:Smoother`を構築します。

行列A[i,j]のスムーズバージョンは次のように定義されます。

$$
A[t, j] = \frac{1}{S_T} \sum_{s=max{t-T,-ξ}}^{min{t-1, ξ}} A[t-s,j]
$$

ここで、$S_T = (2\xi+1)/2$はバンド幅です。
