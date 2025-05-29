```
eFAST(; num_harmonics::Int = 4)
```

  * `num_harmonics`: フーリエ級数分解で合計する調和数、デフォルトは4です。

## メソッドの詳細

eFASTは、特にサンプルサイズが小さい場合に堅牢で、計算効率の良い手法を提供し、Sobolで議論された最初および総合順位インデックスを取得します。これは、曲線に沿った一元的なフーリエ分解を利用し、パラメータ空間を探索します。曲線は一連のパラメトリック方程式によって定義されます。

$$
x_{i}(s) = G_{i}(sin ω_{i}s), ∀ i=1,2 ,..., N
$$

ここで、sは範囲 $-∞ < s < +∞$ で変化するスカラー変数、$G_{i}$ は変換関数、${ω_{i}}, ∀ i=1,2,...,N$ は、すべての $N$（`samples`）のパラメータセットに関連付けられた適切に選択された異なる（角）周波数のセットです。使用される変換やその他の実装の詳細については、[ A. Saltelli et al.](https://dx.doi.org/10.1080/00401706.1999.10485594)を参照してください。

## API

```
gsa(f, method::eFAST, p_range::AbstractVector; samples::Int, batch = false,
         distributed::Val{SHARED_ARRAY} = Val(false),
         rng::AbstractRNG = Random.default_rng(), kwargs...) where {SHARED_ARRAY}
```

注意、`p_range`は上限と下限のタプルのベクターまたは`Distribution`のベクターです。

### 例

以下に、Ishigami関数に対する`eFAST`の使用例を示します。

```julia
using GlobalSensitivity, QuasiMonteCarlo, Distributions

function ishi(X)
    A= 7
    B= 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

## 上限と下限を定義、すなわち一様分布
lb = -ones(4)*π
ub = ones(4)*π

res1 = gsa(ishi, eFAST(), [[lb[i],ub[i]] for i in 1:4], samples=15000)

# 入力の分布を定義
input_ranges = [Normal(0, 1),
                Uniform(-π, π),
                Uniform(-π, π),
                Uniform(-π, π)]

res2 = gsa(ishi, eFAST(), input_ranges, samples=15000)

## バッチ処理を使用
function ishi_batch(X)
    A= 7
    B= 0.1
    @. sin(X[1,:]) + A*sin(X[2,:])^2+ B*X[3,:]^4 *sin(X[1,:])
end

res3 = gsa(ishi_batch, eFAST(), [[lb[i],ub[i]] for i in 1:4], samples=15000, batch=true)
```
