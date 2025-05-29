```
RSA(; n_dummy_parameters::Int = 10, acceptance_threshold::Union{Function, Real} = mean)
```

  * `n_dummy_parameters`: モデルに追加するダミーパラメータの数で、感度仮説検定やサンプル数の確認に使用されます。デフォルトは10です。
  * `acceptance_threshold`: 感度出力の受け入れ分布を定義するためのしきい値またはしきい値を計算する関数です。この関数は、f(Y) の形式であり、Y は与えられた感度基準の出力で、実数を返す必要があります。デフォルトは感度値の平均です。

## メソッドの詳細

RSA（地域感度分析）メソッド[^1]は、非パラメトリックなグローバル感度分析を行うためのモンテカルロベースの手法です。この手法は、連続した1次元確率分布の等価性の非パラメトリックテストであるコルモゴロフ-スミルノフ（KS）テストに基づいています。モンテカルロシミュレーションの各結果は、行動（$B$）または非行動（$\bar{B}$）として分類されます。各パラメータ$i$について、行動出力と非行動出力の累積分布はそれぞれ$F_{i}$と$\bar{F}_{i}$として決定されます。各パラメータ$i$の感度は次のように与えられます：

$$
S_{i} = \sup_{j} |F_{i,j} - (1 - F_{i,j})|
$$

ここで、$F_{i,j}$はパラメータ$i$の感度出力の累積分布のサンプル$j$です。

ダミーパラメータは、サンプル数を確認し、感度仮説検定を行うためにモデルに追加されます。ランダムサンプリングのため、結果は実行ごとに異なる場合があることに注意してください。

## API

```
gsa(f, method::RSA, p_range; samples, batch = false)
```

`sensitivity indices`を`S`として、ダミーパラメータの平均と標準偏差をタプル`Sd = (<mean>, <std>)`として含む`RSAResult`オブジェクトを返します。

### 例

```julia
using GlobalSensitivity

function ishi_batch(X)
    A= 7
    B= 0.1
    @. sin(X[1,:]) + A*sin(X[2,:])^2+ B*X[3,:]^4 *sin(X[1,:])
end
function ishi(X)
    A= 7
    B= 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

lb = -ones(4)*π
ub = ones(4)*π

res1 = gsa(ishi,RSA(),[[lb[i],ub[i]] for i in 1:4],samples=15000)
res2 = gsa(ishi_batch,RSA(),[[lb[i],ub[i]] for i in 1:4],samples=15000,batch=true)
```

### 参考文献

[^1]: Hornberger, G.M. & Spear, Robert. (1981). An Approach to the Preliminary Analysis of Environmental Systems. J. Environ. Manage.; (United States). 12:1.
