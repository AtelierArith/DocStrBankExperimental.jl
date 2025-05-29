```
Pipeline(component1, component2, ... , componentk; options...)
Pipeline(name1=component1, name2=component2, ..., namek=componentk; options...)
component1 |> component2 |> ... |> componentk
```

指定されたコンポーネントを順番に合成する複合モデルタイプのインスタンスを作成します。これは、`component1`が入力を受け取り、その出力が`component2`に渡され、さらにその先へと続くことを意味します。「コンポーネント」とは、`Model`インスタンス、モデルタイプ（すぐにそのデフォルトインスタンスに変換される）、または任意の呼び出し可能オブジェクトのいずれかです。ここでのモデルの「出力」とは、`Supervised`の場合は`predict`が返すもの、`Unsupervised`の場合は`transform`が返すものです。

コンポーネントフィールドの名前は、明示的に指定されない限り自動的に生成されます。例えば、

```julia
Pipeline(encoder=ContinuousEncoder(drop_last=false),
         stand=Standardizer())
```

`Pipeline`コンストラクタは、以下でさらに説明するキーワード`options`を受け入れます。

通常の関数（および他の呼び出し可能なもの）は、以下の例のようにパイプラインに挿入できます。

```
Pipeline(X->coerce(X, :age=>Continuous), OneHotEncoder, ConstantClassifier)
```

### 構文シュガー

`|>`演算子は、モデル、呼び出し可能なもの、および既存のパイプラインからパイプラインを構築するためにオーバーロードされています。

```julia
LinearRegressor = @load LinearRegressor pkg=MLJLinearModels add=true
PCA = @load PCA pkg=MultivariateStats add=true

pipe1 = MLJBase.table |> ContinuousEncoder |> Standardizer
pipe2 = PCA |> LinearRegressor
pipe1 |> pipe2
```

コンポーネントのうち、最大1つだけが監視モデルであることができますが、このモデルは任意の位置に現れることができます。`Supervised`コンポーネントを持つパイプラインは自体が`Supervised`であり、`predict`操作を実装します。それ以外の場合は`Unsupervised`（場合によっては`Static`）であり、`transform`を実装します。

### 特別な操作

すべての`components`が可逆な非監視モデル（すなわち、`inverse_transform`を実装する）である場合、パイプラインに対して`inverse_transform`が実装されます。監視モデルがない場合でも、`predict`は実装されますが、最後のコンポーネントがそれを実装するモデルであると仮定します（いくつかのクラスタリングモデル）。同様に、監視パイプラインで`transform`を呼び出すと、監視コンポーネントの`transform`が呼び出されます。

### トレーニングにターゲットを必要とする変換器

タイプが`Unsupervised`の一部の変換器（したがって、`transform`の出力がパイプラインで伝播される）は、トレーニングのためにターゲット変数を必要とする場合があります。例としては、いわゆるターゲットエンコーダー（いくつかのターゲット観測に基づいてカテゴリカル入力特徴を変換する）が挙げられます。これらのモデルは、パイプライン内の任意の`Supervised`コンポーネントの前に現れる限りサポートされます。もちろん、`Supervised`コンポーネントを含むかどうかにかかわらず、そのようなパイプラインをトレーニングする際にはターゲットを提供する必要があります。

### オプションのキーワード引数

  * `prediction_type`  - パイプラインの予測タイプ; 可能な値: `:deterministic`, `:probabilistic`, `:interval`（推測できない場合のデフォルト=`:deterministic`）
  * `operation` - 存在する場合、監視コンポーネントモデルに適用される操作; 可能な値: `predict`, `predict_mean`, `predict_median`, `predict_mode`（デフォルト=`predict`）
  * `cache` - コンポーネントモデルのために作成された内部マシンがデータのモデル固有の表現をキャッシュすべきかどうか（[`machine`](@ref)を参照）（デフォルト=`true`）

!!! warning
    データの匿名化を保証するために`cache=false`を設定してください。


より複雑な非分岐パイプラインを構築するには、モデルの合成に関するMLJマニュアルのセクションを参照してください。 ```
