```
random_undersample(
    X, y; 
    ratios=1.0, rng=default_rng(), 
    try_preserve_type=true
)
```

# 説明

既存の観測値をランダムに削除することによって、データセットを単純にアンダーサンプリングします。

# 位置引数

  * `X`: 実数の行列または、`Union{Finite, Infinite}`をサブタイプとする要素を持つテーブル。名義列の要素は`Finite`をサブタイプとする必要があります（すなわち、[scitype](https://juliaai.github.io/ScientificTypes.jl/)が`OrderedFactor`または`Multiclass`である必要があります）し、連続列の要素は`Infinite`をサブタイプとする必要があります（すなわち、[scitype](https://juliaai.github.io/ScientificTypes.jl/)が`Count`または`Continuous`である必要があります）。
  * `y`: `X`の観測値に対応するラベルの抽象ベクトル（例：文字列）

# キーワード引数

  * `ratios=1.0`: 各クラスのアンダーサンプリングの量を制御するパラメータ

      * 浮動小数点数である場合、各クラスはマイノリティクラスのサイズに浮動小数点数を掛けたサイズにアンダーサンプリングされます。デフォルトでは、すべてのクラスがマイノリティクラスのサイズにアンダーサンプリングされます。
      * 各クラスラベルをそのクラスの浮動小数点比率にマッピングする辞書であることもできます。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `AbstractRNG`オブジェクトまたは、Julia `VERSION`がサポートしている場合に`Xoshiro`で使用される整数シード。そうでない場合は、MersenneTwisterを使用します。
  * `try_preserve_type::Bool=true`: `true`の場合、関数は入力テーブル（例：`DataFrame`）の型を変更しないように試みます。ただし、一部のテーブルでは成功しない場合があり、その場合、返されるテーブルは列テーブル（ベクトルの名前付きタプル）になります。このパラメータは、入力が行列の場合は無視されます。

# 戻り値

  * `X_under`: 入力`X`が行列またはテーブルであるかに応じて、アンダーサンプリング後のデータを含む行列またはテーブル
  * `y_under`: `X_under`に対応するラベルの抽象ベクトル

# 例

```julia
using Imbalance

# 各クラスの確率を設定
class_probs = [0.5, 0.2, 0.3]                         
num_rows, num_continuous_feats = 100, 5
# それに応じてテーブルとカテゴリカルベクトルを生成
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                class_probs, rng=42)   

julia> Imbalance.checkbalance(y; ref="minority")
 1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
 2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (173.7%) 
 0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (252.6%) 

# ランダムアンダーサンプリングを適用
X_under, y_under = random_undersample(X, y; ratios=Dict(0=>1.0, 1=> 1.0, 2=>1.0), 
                                      rng=42)
                                      
julia> Imbalance.checkbalance(y_under; ref="minority")
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
```

# MLJモデルインターフェース

キーワード引数を`RandomUndersampler`モデルの初期化時に渡し、位置引数`X, y`を`transform`メソッドに渡します。

```julia
using MLJ
RandomUndersampler = @load RandomUndersampler pkg=Imbalance

# モデルをマシンでラップ
undersampler = RandomUndersampler(ratios=Dict(0=>1.0, 1=> 1.0, 2=>1.0), 
               rng=42)
mach = machine(undersampler)

# 変換するデータを提供（フィットする必要はありません）
X_under, y_under = transform(mach, X, y)
```

この`MLJ`インターフェースについては、MLJの[モデルブラウザ](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/)からアクセスしてさらに読むことができます。

# TableTransformsインターフェース

このインターフェースは、入力が1つのテーブル`Xy`であり、`y`がその列の1つであることを前提としています。したがって、コンストラクタには整数`y_ind`を指定して、`y`がどの列であるかを指定する必要があります。他のキーワード引数はその後に続きます。変換を適用する際には、`Xy`のみが提供されます。

```julia
using Imbalance
using Imbalance.TableTransforms

# 不均衡データを生成
num_rows = 100
num_features = 5
y_ind = 3
Xy, _ = generate_imbalanced_data(num_rows, num_features; 
                                 class_probs=[0.5, 0.2, 0.3], insert_y=y_ind, rng=42)

# ランダムアンダーサンプリングモデルを初期化
undersampler = RandomUndersampler(y_ind; ratios=Dict(0=>1.0, 1=>1.0, 2=>1.0), rng=42)
Xy_under = Xy |> undersampler                    
Xy_under, cache = TableTransforms.apply(undersampler, Xy)    # 同等
```

`TableTransforms`の`reapply(undersampler, Xy, cache)`メソッドは、単に`apply(undersample, Xy)`に戻り、`revert(undersampler, Xy, cache)`はサポートされていません。

# イラストレーション

完全な基本例とアニメーションは[こちら](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/undersample_random.ipynb)で見つけることができます。より実用的な例は、[チュートリアル](https://juliaai.github.io/Imbalance.jl/dev/examples/)セクションにあり、Google Colabでのコードの実行についても説明しています。
