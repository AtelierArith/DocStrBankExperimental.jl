```
bwsj(X; rtol=0.1, leafsize=10, lower=λ*n^(-1/5)*1e-9, upper=λ*n^(-1/5)*1e9)
```

ガウスカーネルを使用したカーネル密度推定のためのバンド幅選択。論文 Sheather, S. J., & Jones, M. C. (1991). A reliable data‐based bandwidth selection method for kernel density estimation. Journal of the Royal Statistical Society: Series B (Methodological), 53(3), 683-690. に基づいています。

方程式 [ R(K) / (nσ⁴ₖS_D(α₂(h))) ]^(1/5) - h = 0 を根探索によって解き、目的関数の符号が知られているときに各反復を終了できるように目的を制約します。

  * `rtol` - バンド幅の相対許容誤差。
  * `leafsize` - このサイズ未満では、境界の代わりに正確な計算が使用されます。結果の精度には影響しませんが、実行時間には影響します。
  * `lower` - バンド幅の下限。境界を変更する必要は通常ありません。
  * `upper` - バンド幅の上限。
