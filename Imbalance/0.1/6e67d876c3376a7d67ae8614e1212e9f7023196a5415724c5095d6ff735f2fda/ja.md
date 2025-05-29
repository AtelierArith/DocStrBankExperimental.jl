```
random_walk_oversample(
	X, y, cat_inds;
	ratios=1.0, rng=default_rng(),
	try_preserve_type=true
)
```

# 説明

[1]で提示されたランダムウォークオーバーサンプリングを使用してデータセットをオーバーサンプリングします。

# 位置引数

  * `X`: 浮動小数点数の行列または、`Union{Finite, Infinite}`のサブタイプを持つ要素を含むテーブル。名義列の要素は`Finite`のサブタイプである必要があります（すなわち、`OrderedFactor`または`Multiclass`のscitypeを持つ）し、連続列の要素は`Infinite`のサブタイプである必要があります（すなわち、`Count`または`Continuous`のscitypeを持つ）。
  * `y`: `X`の観測に対応するラベル（例えば、文字列）の抽象ベクトル
  * `cat_inds::AbstractVector{<:Int}`: 名義特徴のインデックスのベクトル。`X`が行列の場合のみ提供されます。そうでない場合、テーブルのscitypesから推測されます。

# キーワード引数

  * `ratios=1.0`: 各クラスのオーバーサンプリングの量を制御するパラメータ

      * 浮動小数点数である場合、この場合、各クラスは多数派クラスのサイズに浮動小数点数を掛けたサイズにオーバーサンプリングされます。デフォルトでは、すべてのクラスが多数派クラスのサイズにオーバーサンプリングされます。
      * 各クラスラベルをそのクラスの浮動小数点比率にマッピングする辞書であることもできます。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `AbstractRNG`オブジェクトまたは、Julia `VERSION`がサポートしている場合に`Xoshiro`で使用される`Integer`シード。そうでない場合、`MersenneTwister`を使用します。
  * `try_preserve_type::Bool=true`: `true`の場合、関数は入力テーブル（例えば、`DataFrame`）の型を変更しないように試みます。ただし、一部のテーブルではこれが成功しない場合があり、その場合、返されるテーブルは列テーブル（ベクトルの名前付きタプル）になります。このパラメータは、入力が行列の場合は無視されます。

# 戻り値

  * `Xover`: オリジナルデータとオーバーサンプリングによる新しい観測を含む行列またはテーブル。入力`X`が行列またはテーブルであるかによって異なります。
  * `yover`: `Xover`に対応するラベルの抽象ベクトル

# 例

```julia
using Imbalance
using ScientificTypes

# 各クラスの確率を設定
class_probs = [0.5, 0.2, 0.3]                         
num_rows = 100
num_continuous_feats = 3
# それぞれ3つと2つの可能な値を持つ2つのカテゴリ特徴を希望
num_vals_per_category = [3, 2]

# テーブルとカテゴリベクトルを生成
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                class_probs, num_vals_per_category, rng=42)    
								                  
julia> Imbalance.checkbalance(y)
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (39.6%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (68.8%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 

julia> ScientificTypes.schema(X).scitypes
(Continuous, Continuous, Continuous, Continuous, Continuous)
# 名義列を有限のscitype（マルチクラスまたは順序因子）に強制変換
X = coerce(X, :Column4=>Multiclass, :Column5=>Multiclass)

# ランダムウォークオーバーサンプリングを適用
Xover, yover = random_walk_oversample(X, y; 
                                      ratios = Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng = 42)

julia> Imbalance.checkbalance(yover)
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 38 (79.2%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 43 (89.6%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 
```

# MLJモデルインターフェース

`RandomWalkOversampling`モデルを初期化する際にキーワード引数を渡し、`cat_inds`を除く位置引数を`transform`メソッドに渡します。

```julia
using MLJ
RandomWalkOversampler = @load RandomWalkOversampler pkg=Imbalance

# モデルをマシンにラップ
oversampler = RandomWalkOversampler(ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
mach = machine(oversampler)

# 変換するデータを提供（フィットするものはありません）
Xover, yover = transform(mach, X, y)
```

この`MLJ`インターフェースについては、MLJの[モデルブラウザ](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/)からアクセスしてさらに読むことができます。このメソッドのMLJインターフェースでは、`Table`入力のみがサポートされていることに注意してください。

# TableTransformsインターフェース

このインターフェースは、入力が1つのテーブル`Xy`であり、`y`がその列の1つであることを前提としています。したがって、コンストラクタには整数`y_ind`を指定して、どの列が`y`であるかを指定する必要があります。他のキーワード引数はその後に続きます。変換を適用する際には、`Xy`のみが提供されます。

```julia
using Imbalance
using ScientificTypes
using Imbalance.TableTransforms

# 不均衡データを生成
num_rows = 100
num_continuous_feats = 3
y_ind = 2

# テーブルとカテゴリベクトルを生成
Xy, _ = generate_imbalanced_data(num_rows, num_continuous_feats; insert_y=y_ind,
                                class_probs= [0.5, 0.2, 0.3], num_vals_per_category=[3, 2],
                                 rng=42)  

# テーブルは有限または連続のscitypesのみを持つ必要があります                                
Xy = coerce(Xy, :Column2=>Multiclass, :Column5=>Multiclass, :Column6=>Multiclass)

# ランダムウォークオーバーサンプリングモデルを初期化
oversampler = RandomWalkOversampler(y_ind;
                                    ratios=Dict(1=>1.0, 2=> 0.9, 3=>0.9), rng=42)
Xyover = Xy |> oversampler                               
# TableTransformsが使用される場合は同等
Xyover, cache = TableTransforms.apply(oversampler, Xy)    # 同等
```

# イラストレーション

完全な基本例とアニメーションは[こちら](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/oversample_randomwalk.ipynb)で見つけることができます。より実用的な例は、[チュートリアル](https://juliaai.github.io/Imbalance.jl/dev/examples/)セクションにあり、Google Colabでのコードの実行についても説明しています。

# 参考文献

[1] Zhang, H., & Li, M. (2014). RWO-Sampling: A random walk over-sampling approach to imbalanced data classification.  Information Fusion, 25, 4-20.
