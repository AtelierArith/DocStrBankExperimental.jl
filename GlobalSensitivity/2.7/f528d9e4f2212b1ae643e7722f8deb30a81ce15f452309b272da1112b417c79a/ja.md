```
EASI(; max_harmonic::Int = 10, dct_method::Bool = false)
```

  * `max_harmonic`: 出力パワースペクトルが分析される入力周波数の最大ハーモニクス。デフォルトは10。
  * `dct_method`: パワースペクトルを計算するために離散コサイン変換法を使用します。デフォルトはfalse。

## メソッドの詳細

EASIメソッドは、最初のオーダー効果（Sobol'インデックス）の計算のためのグローバル感度分析の分散ベースの手法を実行するためのフーリエベースの技術であり、FASTやRBDと同じクラスのアルゴリズムに属します。これは、既存のデータを使用できる計算コストの低い方法です。入力要因のための適切な周波数データを含む特別に生成されたサンプルセットを使用するFASTおよびRBDメソッドとは異なり、EASIでは利用可能な入力サンプルをソートおよびシャッフルすることによってこれらの周波数が導入されます。

## API

```
gsa(f, method::EASI, p_range; samples, batch = false)
gsa(X, Y, method::EASI)
```

### 例

```julia
using GlobalSensitivity, Test

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

res1 = gsa(ishi,EASI(),[[lb[i],ub[i]] for i in 1:4],samples=15000)
res2 = gsa(ishi_batch,EASI(),[[lb[i],ub[i]] for i in 1:4],samples=15000,batch=true)

X = QuasiMonteCarlo.sample(15000, lb, ub, QuasiMonteCarlo.SobolSample())
Y = ishi.([X[:, i] for i in 1:15000])

res1 = gsa(X, Y, EASI())
res1 = gsa(X, Y, EASI(; dct_method = true))
```
