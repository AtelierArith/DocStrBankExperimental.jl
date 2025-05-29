```
hampel(x, K; spread=mad, threshold=2, boundary=:truncate)
```

時系列にウィンドウ付きハンペルフィルタを適用します。

ベクトル `x` と半幅 `K` が与えられたとき、幅 2K+1 のスライディングウィンドウ内でハンペル基準を適用します。ウィンドウの中央値 $m$ は、次の条件を満たす場合にウィンドウの中心にある要素 $xₖ$ を置き換えます。

$$
|xₖ - m| > t S,
$$

ここで、分散スケール $S$ は関数 `spread` によって提供され、パラメータ $t$ は `threshold` によって与えられます。ウィンドウは、ベクトルの先頭と末尾近くで短くなり、架空の要素を参照しないようにします。大きな値の $t$ はフィルタをあまり攻撃的でなくし、$t=0$ は標準の中央値フィルタです。

再帰的フィルタリングについては `hampel!` を参照してください。

`boundary` の値は、フィルタがベクトルの境界をどのように処理するかを決定します：

  * `:truncate` (デフォルト)：境界でウィンドウが短くなります
  * `:reflect`：値が境界を越えて反射されます
  * `:repeat`：必要に応じて端の値が繰り返されます

```
hampel(x, weights; ...)
```

時系列に重み付きハンペルフィルタを適用します。

ベクトル `x` と正の整数のベクトル `weights` が与えられたとき、基準を計算する前にウィンドウ内の各要素は、その対応する重みで与えられた回数だけ繰り返されます。これは通常、中央の要素を他の要素よりも影響力のあるものにするために使用されます。

### クレジット

この関数は https://github.com/tobydriscoll/HampelOutliers.jl から適応されており、詳細や例については元のソースを参照してください。元の `HampelOutliers.jl` 関数との違いは、ここで `Hampel.identify` と `Hampel.filter` の異なるメソッドを作成し、それらをまとめて $hampel$ と呼び、マルチディスパッチに作業をさせたことです。

### 例

```julia
t = (1:50) / 10; x = [1:2:40; 5t + (@. 6cos(t + 0.5(t)^2)); fill(40,20)];
x[12] = -10; x[50:52] .= -12; x[79:82] .= [-5, 50, 55, 0];
plot(x, marker=:point, mc=:blue, lc=:blue, label="Original", xlabel="k", ylabel="x_k")
scatter!(m, ms="2p", mc=:red, MarkerEdgeColor=true, label="Median filter")
scatter!(y, ms="2p", mc=:green, MarkerEdgeColor=true, label="Hampel filter", show=true)
```
