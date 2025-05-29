```
UnivariateBoxCoxTransformer
```

単一変数のBox-Cox変換器を構築するためのモデルタイプで、[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
UnivariateBoxCoxTransformer = @load UnivariateBoxCoxTransformer pkg=MLJModels
```

`model = UnivariateBoxCoxTransformer()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`UnivariateBoxCoxTransformer(n=...)`のようにキーワード引数を提供します。

Box-Cox変換は、データをより正規分布に近づけることを試みます。これにより、パフォーマンスが向上し、データが正規分布によって生成されると仮定するモデルの解釈が助けられます。

Box-Cox変換（シフトあり）は次の形式です。

```
x -> ((x + c)^λ - 1)/λ
```

ここで、`c`は定数、`λ`は実数ですが、`λ = 0`の場合は、上記は次のように置き換えられます。

```
x -> log(x + c)
```

ユーザー指定のハイパーパラメータ`n::Integer`と`shift::Bool`に基づいて、現在の実装はトレーニングデータからパラメータ`c`と`λ`を学習します。`shift=true`でデータにゼロが含まれている場合、`c`はデータの平均の`0.2`倍に設定されます。ゼロがない場合は、シフトは適用されません。最後に、`-0.4`から`3`の間の`n`個の異なる`λ`の値が考慮され、変換されたデータの正規性を最大化する値に`λ`が固定されます。

*参考文献:* [パワー変換のWikipediaエントリ](https://en.wikipedia.org/wiki/Power_transform)。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, x)
```

ここで

  * `x`: 要素のscitypeが`Continuous`の任意の抽象ベクター; `scitype(x)`でscitypeを確認します

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `n=171`: 試すべき指数`λ`の値の数
  * `shift=false`: ゼロが存在する場合に変換に予備の定数変換を含めるかどうか

# 操作

  * `transform(mach, xnew)`: `mach`をフィッティングする際に学習したBox-Cox変換を適用します
  * `inverse_transform(mach, z)`: `mach`によって学習された変換が`z`であるベクトル`z`を再構築します

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `λ`: 学習されたBox-Cox指数
  * `c`: 学習されたシフト

# 例

```
using MLJ
using UnicodePlots
using Random
Random.seed!(123)

transf = UnivariateBoxCoxTransformer()

x = randn(1000).^2

mach = machine(transf, x)
fit!(mach)

z = transform(mach, x)

julia> histogram(x)
                ┌                                        ┐
   [ 0.0,  2.0) ┤███████████████████████████████████  848
   [ 2.0,  4.0) ┤████▌ 109
   [ 4.0,  6.0) ┤█▍ 33
   [ 6.0,  8.0) ┤▍ 7
   [ 8.0, 10.0) ┤▏ 2
   [10.0, 12.0) ┤  0
   [12.0, 14.0) ┤▏ 1
                └                                        ┘
                                 Frequency

julia> histogram(z)
                ┌                                        ┐
   [-5.0, -4.0) ┤█▎ 8
   [-4.0, -3.0) ┤████████▊ 64
   [-3.0, -2.0) ┤█████████████████████▊ 159
   [-2.0, -1.0) ┤█████████████████████████████▊ 216
   [-1.0,  0.0) ┤███████████████████████████████████  254
   [ 0.0,  1.0) ┤█████████████████████████▊ 188
   [ 1.0,  2.0) ┤████████████▍ 90
   [ 2.0,  3.0) ┤██▊ 20
   [ 3.0,  4.0) ┤▎ 1
                └                                        ┘
                                 Frequency

```
