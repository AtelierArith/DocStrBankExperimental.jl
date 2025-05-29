MutualInformation(; n*bootstraps = 1000, conf*level = 0.95)

  * `n_bootstraps`: 帰納分布の推定に使用されるブートストラップの数。デフォルトは `1000`。
  * `conf_level`: 最小境界推定の信頼レベル。デフォルトは `0.95`。

## メソッドの詳細

相互情報量に基づく感度分析は、情報理論的尺度に基づく感度分析の代替アプローチです。この方法では、出力分布のエントロピーによって出力の不確実性が定量化され、分散ベースのアプローチを取るのではありません。出力のシャノンエントロピーは次のように与えられます：

$$
H(Y) = -\sum_y p(y) \log p(y)
$$

ここで、$p(y)$ は出力 $Y$ の確率密度関数です。入力 $X_i$ を固定することにより、出力 $Y$ の条件付きエントロピーは次のように与えられます：

$$
H(Y|X_i) = -\sum_{x} p(x) H(Y|X_i = x)
$$

入力 $X_i$ と出力 $Y$ の間の相互情報量は次のように与えられます：

$$
I(X_i;Y) = H(Y) - H(Y|X_i) = H(X) + H(Y) - H(X,Y)
$$

ここで、$H(X,Y)$ は入力と出力の結合エントロピーです。相互情報量は入力パラメータの感度指数を計算するために使用できます。

### 感度指数

感度指数は、出力の帰納分布の $\alpha$ 分位点が相互情報量から引かれる形で、入力 $X_i$ と出力 $Y$ の間の相互情報量として計算されます：

$$
S_{1,i} = I(X_i;Y) - Q(I(X_i; Y_\text{null}), \alpha)
$$

感度分析に相互情報量を使用することは、Lüdtke et al. (2007)[^1] で紹介され、Datseris & Parlitz (2022)[^2] にも記載されています。

## API

```
gsa(f, method::MutualInformation, p_range; samples, batch = false)
```

`MutualInformationResult` オブジェクトを返し、パラメータの結果の感度指数と対応する信頼区間を含みます。`MutualInformationResult` オブジェクトには次のフィールドが含まれます：

  * `S`: 感度指数。
  * `mutual_information`: 計算された相互情報量の値
  * `bounds`: 相互情報量の帰納分布の計算された上限。

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

res1 = gsa(ishi,MutualInformation(),[[lb[i],ub[i]] for i in 1:4],samples=15000)
res2 = gsa(ishi_batch,MutualInformation(),[[lb[i],ub[i]] for i in 1:4],samples=15000,batch=true)
```

### 参考文献

[^1]: Lüdtke, N., Panzeri, S., Brown, M., Broomhead, D. S., Knowles, J., Montemurro, M. A., & Kell, D. B. (2007). Information-theoretic sensitivity analysis: a general method for credit assignment in complex networks. Journal of The Royal Society Interface, 5(19), 223–235.

[^2]: Datseris, G., & Parlitz, U. (2022). Nonlinear Dynamics, Ch. 7, pg. 105-119.
