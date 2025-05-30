```
DGSM(; crossed::Bool = false)
```

  * `crossed`: DGSMの交差インデックスの計算のための指標として機能するブール値。

## メソッドの詳細

DGSMメソッドは、各パラメータの確率分布を取り、分布からサンプルを取得してランダムなパラメータセットを作成します。次に、分析対象の関数の導関数がサンプルされたパラメータで計算され、その導関数の特定の統計が使用されます。[Sobol and Kucherenko](https://www.sciencedirect.com/science/article/pii/S0378475409000354)による論文では、DGSMの結果、`tao`および`sigma`とMorrisの基本的効果およびSobolインデックスとの関係について論じられています。

## API

```
gsa(f, method::DGSM, distr::AbstractArray; samples::Int, kwargs...)
```

  * `dist`: 各変数の分布の配列。例えば、2つの変数のために`dist = [Normal(5,6),Uniform(2,3)]`のようにします。

### 例

```julia
using GlobalSensitivity, Test, Distributions

samples = 2000000

f1(x) = x[1] + 2*x[2] + 6.00*x[3]
dist1 = [Uniform(4,10),Normal(4,23),Beta(2,3)]
b =  gsa(f1,DGSM(),dist1,samples=samples)
```
