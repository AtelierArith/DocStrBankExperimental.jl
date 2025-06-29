```
shapley(predict, a, X)
shapley(predict, a, X, j)
shapley(predict, a, X, Z)
shapley(predict, a, X, j, Z)
```

データセット `Z` のポイントのシャプレー値を計算します。データセット `X` は、`Z` のポイントの分布の経験的推定として使用されます。`Z` が提供されていない場合、シャプレー値は `X` のポイントに対して計算されます。シャプレー値を計算するためのさまざまな非同値の方法があり、これらは `a` で指定される `Shapley.Algorithm` オブジェクトによって計算方法が決まります。`predict` 関数はデータセットに対して予測を行うために使用されます。評価されるモデルオブジェクトは `predict` 関数を介してエンコードされます。

`predict` によって返される予測が決定論的であり、したがって数値の配列である場合、返されるシャプレー値は数値になります。予測が確率的である場合、`predict` は `Distributions.Sampleable` オブジェクトの配列を返すことが期待され、`Shapley` はテーブルを返します。このテーブルの列は、`Distributions.support` によって決定される分布のドメインに従って名前が付けられます。

すべてのアルゴリズムは、`predict` 関数がデータのバッチで操作する際に最も効率的であると仮定します。つまり、`predict` への個別の呼び出しの数を最小限に抑えようとします。

詳細や例については、[Shapley.jl ドキュメント](https://expandingman.gitlab.io/Shapley.jl/)を参照してください。

## 引数

  * `predict`: Tables 互換オブジェクト（または行列）を受け取り、決定論的な予測を実数としてのベクトルで返すか、確率的な予測を `Distributions.Sampleable` オブジェクトとして返す関数。
  * `a`: 計算がどのように行われるべきかを指定する `Shapley.Algorithm` オブジェクト。利用可能なアルゴリズムのリストについては `subtypes(Shapley.Algorithm)` を参照してください。
  * `X`: シャプレーアルゴリズムが独立変数の分布の経験的推定を提供するために使用する入力データセット。通常、これはテストセットまたはトレーニングセットです。
  * `j`: シャプレー値を計算する特徴で、`X` の列として指定します。整数または `Symbol` である必要があります。提供されない場合、シャプレー値はすべての列に対して計算されます。
  * `Z`: シャプレー値を計算するデータポイントのセット。提供されない場合、`X` が使用されます。

## 例

```julia
m = machine(RandomForestRegressor(), X, y)  # MLJ マシンオブジェクト
ϕ = shapley(ξ -> predict(m, ξ), Shapley.MonteCarlo(512), X)
```
