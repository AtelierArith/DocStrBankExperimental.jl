```
TransformedTargetModel(model; transformer=nothing, inverse=nothing, cache=true)
```

教師ありまたは半教師ありの `model` をターゲット変数の変換でラップします。

ここで `transformer` は次のいずれかです：

  * トレーニングターゲットを変換するための `Unsupervised` モデル。デフォルトでは（`inverse=nothing`）、このトランスフォーマーによって学習されたパラメータも `model` の予測を逆変換するために使用されます。つまり、`transformer` は `inverse_transform` メソッドを実装している必要があります。そうでない場合は、逆変換を抑制するために `inverse=identity` を指定してください。
  * ターゲットを変換するための呼び出し可能なオブジェクト、例えば `y -> log.(y)` のようなもの。この場合、呼び出し可能な `inverse`、例えば `z -> exp.(z)` を指定する必要があります。

メモリを速度よりも優先する場合やデータの匿名性を保証する場合は、`cache=false` を指定してください。

`model` が確率的予測器である場合は、逆変換によるサンプル空間の変換はサポートされていないため、`inverse=identity` を指定してください。あるいは、`model` を決定論的モデル（例えば `Pipeline(model, y -> mode.(y))`）に置き換えてください。

### 例

ターゲットを正規化してからリッジ回帰を適用し、予測を元のスケールで返すモデル：

```julia
@load RidgeRegressor pkg=MLJLinearModels
model = RidgeRegressor()
tmodel = TransformedTargetModel(model, transformer=Standardizer())
```

データに静的な `log` 変換を適用し、再び予測を元のスケールで返すモデル：

```julia
tmodel2 = TransformedTargetModel(model, transformer=y->log.(y), inverse=z->exp.(y))
```
