```
RandomSearch(bounded=Distributions.Uniform,
             positive_unbounded=Distributions.Gamma,
             other=Distributions.Normal,
             rng=Random.GLOBAL_RNG)
```

Cartesianハイパーパラメータドメインを検索するためのランダムサーチチューニング戦略をインスタンス化し、各次元でカスタマイズ可能な事前分布を持ちます。

### サポートされている範囲

単一の1次元範囲または1次元範囲のベクトルを指定できます。事前分布とペアになっていない場合、チューニング戦略のハイパーパラメータで指定されたフォールバック分布タイプに従って1つがフィッティングされます。具体的には、`RandomSearch`では、`TunedModel`インスタンスの`range`フィールドは次のように設定できます：

  * 単一の1次元範囲（`ParamRange`オブジェクト）`r`
  * 形式が`(r, d)`のペアで、`r`は上記の通りで、`d`は：

      * `r.values`と同じ長さの確率ベクトル（`r`は`NominalRange`）
      * 任意の`Distributions.UnivariateDistribution` *インスタンス*（`r`は`NumericRange`）
      * 自動フィッティングのために`Distributions.fit(d, r)`を使用する、`r.lower`と`r.upper`の間に常にサポートがある分布の*サブタイプ*の1つ（`r`は`NumericRange`）
  * 形式が`(field, s)`の任意のペアで、`field`はチューニングされるモデルのフィールドの（ネストされた可能性のある）名前で、`s`はそのフィールドの任意のサンプラーオブジェクトです。これは、`rand(rng, s)`が定義され、そのフィールドの有効な値を返すことを意味します。
  * 上記の形式のオブジェクトの任意のベクトル

範囲ベクトルには、同じモデルフィールドの複数のエントリを含めることができ、例えば`range = [(:lambda, s1), (:alpha, s), (:lambda, s2)]`のようになります。その場合、各イテレーションで使用されるエントリはランダムです。

|                                                                                        分布タイプ | このタイプの範囲にフィッティングするため |
| --------------------------------------------------------------------------------------------:| --------------------:|
| `Arcsine`, `Uniform`, `Biweight`, `Cosine`, `Epanechnikov`, `SymTriangularDist`, `Triweight` |                   有界 |
|                                                        `Gamma`, `InverseGaussian`, `Poisson` |          正（有界または無限大） |
|                             `Normal`, `Logistic`, `LogNormal`, `Cauchy`, `Gumbel`, `Laplace` |                 いずれか |

`ParamRange`オブジェクトは`range`メソッドを使用して構築されます。

### 例

```
using Distributions

range1 = range(model, :hyper1, lower=0, upper=1)

range2 = [(range(model, :hyper1, lower=1, upper=10), Arcsine),
          range(model, :hyper2, lower=2, upper=Inf, unit=1, origin=3),
          (range(model, :hyper2, lower=2, upper=4), Normal(0, 3)),
          (range(model, :hyper3, values=[:ball, :tree]), [0.3, 0.7])]

# NumericRangeを定義せずに[0, 1]からの:(atom.λ)の一様サンプリング：
struct MySampler end
Base.rand(rng::Random.AbstractRNG, ::MySampler) = rand(rng)
range3 = (:(atom.λ), MySampler())
```

### アルゴリズム

各イテレーションで、`model`のディープコピーのフィールドを変異させて評価用のモデルが生成されます。範囲ベクトルはシャッフルされ、新しい順序に従ってフィールドがサンプリングされます（繰り返しフィールドが複数回変異します）。形式が`(field, s)`の`range`エントリの場合、アルゴリズムは`rand(rng, s)`を呼び出し、モデルクローンのフィールド`field`をこの値に変異させます。形式が`(r, d)`のエントリの場合、`s`は`sampler(r, d)`で置き換えられます。`d`が指定されていない場合、`r`が`NominalRange`であればサンプリングは一様（置換あり）であり、そうでなければ`NumericRange`オブジェクト`r`のフィールド値に応じて、チューニング戦略パラメータ`bounded`、`positive_unbounded`、および`other`で指定されたデフォルトが与えられます。

[`TunedModel`](@ref)、[`range`](@ref)、[`sampler`](@ref)も参照してください。
