```
smotenc(
    X, y, split_ind;
    k=5, ratios=1.0, knn_tree="Brute", rng=default_rng(),
    try_preserve_type=true
)
```

# 説明

`SMOTE-NC`（Synthetic Minority Oversampling Techniques-Nominal Continuous）アルゴリズムを使用してデータセットをオーバーサンプリングし、クラスの不均衡を修正します[1]。これは、名義的および連続的な特徴を持つデータセットに対処するための`SMOTE`の変種です。

!!! warning "SMOTE-NCは連続的な特徴が存在することを前提としています"
    データセットが純粋に名義的である場合、SMOTE-NCは機能しません。その場合は、代わりに[SMOTE-N](@ref)を参照してください。 一方、データセットが純粋に連続的である場合、標準の[SMOTE](@ref)と同等です。


# 位置引数

  * `X`: `Union{Finite, Infinite}`のサブタイプである要素を持つ浮動小数点の行列またはテーブル。名義的な列の要素は`Finite`（すなわち、[scitype](https://juliaai.github.io/ScientificTypes.jl/) `OrderedFactor`または`Multiclass`を持つ）である必要があり、連続的な列の要素は`Infinite`（すなわち、[scitype](https://juliaai.github.io/ScientificTypes.jl/) `Count`または`Continuous`を持つ）である必要があります。
  * `y`: `X`の観測に対応するラベルの抽象ベクター（例：文字列）
  * `cat_inds::AbstractVector{<:Int}`: 名義的特徴のインデックスのベクター。`X`が行列の場合のみ提供されます。そうでない場合、テーブルの[scitypes](https://juliaai.github.io/ScientificTypes.jl/)から推測されます。

# キーワード引数

  * `k::Integer=5`: アルゴリズムで考慮する最近傍の数。`0 < k < n`の範囲内である必要があり、ここでnは最小クラスの観測数です。
  * `ratios=1.0`: 各クラスのオーバーサンプリングの量を制御するパラメータ

      * 浮動小数点数である場合、各クラスは多数派クラスのサイズに浮動小数点数を掛けたサイズにオーバーサンプリングされます。デフォルトでは、すべてのクラスが多数派クラスのサイズにオーバーサンプリングされます。
      * 各クラスラベルをそのクラスの浮動小数点比率にマッピングする辞書であることもできます。
  * `knn_tree`: KNN計算で使用されるツリーを決定します。`"Brute"`または`"Ball"`のいずれか。BallTreeははるかに高速ですが、不正確な結果をもたらす可能性があります。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `AbstractRNG`オブジェクトまたは、Julia `VERSION`がサポートしている場合は`Xoshiro`で使用される`Integer`シード。そうでない場合は、MersenneTwisterを使用します。
  * `try_preserve_type::Bool=true`: `true`の場合、関数は入力テーブル（例：`DataFrame`）の型を変更しないように試みます。ただし、一部のテーブルではこれが成功しない場合があり、その場合、返されるテーブルは列テーブル（ベクターの名前付きタプル）になります。このパラメータは、入力が行列の場合は無視されます。

# 戻り値

  * `Xover`: オリジナルデータとオーバーサンプリングによって生成された新しい観測を含む行列またはテーブル。入力`X`が行列またはテーブルのいずれかに応じて異なります。
  * `yover`: `Xover`に対応するラベルの抽象ベクター

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

# テーブルとカテゴリベクターを生成
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                class_probs, num_vals_per_category, rng=42)                      
julia> Imbalance.checkbalance(y)
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (39.6%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (68.8%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 

julia> ScientificTypes.schema(X).scitypes
(Continuous, Continuous, Continuous, Continuous, Continuous)
# 名義的列を有限のscitype（マルチクラスまたは順序付き因子）に強制変換
X = coerce(X, :Column4=>Multiclass, :Column5=>Multiclass)

# SMOTE-NCを適用
Xover, yover = smotenc(X, y; k = 5, ratios = Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng = 42)

julia> Imbalance.checkbalance(yover)
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 38 (79.2%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 43 (89.6%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 
```

# MLJモデルインターフェース

`SMOTENC`モデルを初期化する際にキーワード引数を渡し、`cat_inds`を除く位置引数を`transform`メソッドに渡します。

```julia
using MLJ
SMOTENC = @load SMOTENC pkg=Imbalance

# モデルをマシンにラップ
oversampler = SMOTENC(k=5, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
mach = machine(oversampler)

# 変換するデータを提供（フィットするものはありません）
Xover, yover = transform(mach, X, y)
```

この`MLJ`インターフェースについては、MLJの[モデルブラウザ](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/)からアクセスしてさらに読むことができます。このメソッドのMLJインターフェースでは、`Table`入力のみがサポートされていることに注意してください。

# TableTransformsインターフェース

このインターフェースは、入力が1つのテーブル`Xy`であり、`y`がその列の1つであることを前提としています。したがって、コンストラクタには整数`y_ind`を指定して、`y`がどの列であるかを指定する必要があります。他のキーワード引数はその後に続きます。変換を適用する際には、`Xy`のみが提供されます。

```julia
using Imbalance
using ScientificTypes
using Imbalance.TableTransforms

# 不均衡データを生成
num_rows = 100
num_continuous_feats = 3
y_ind = 2
# テーブルとカテゴリベクターを生成
Xy, _ = generate_imbalanced_data(num_rows, num_continuous_feats; insert_y=y_ind,
                                class_probs= [0.5, 0.2, 0.3], num_vals_per_category=[3, 2],
                                 rng=42)  

# テーブルは有限または連続のscitypesのみを持つ必要があります                                
Xy = coerce(Xy, :Column2=>Multiclass, :Column5=>Multiclass, :Column6=>Multiclass)

# SMOTENCモデルを初期化
oversampler = SMOTENC(y_ind; k=5, ratios=Dict(1=>1.0, 2=> 0.9, 3=>0.9), rng=42)
Xyover = Xy |> oversampler                               
# TableTransformsが使用される場合は同等です
Xyover, cache = TableTransforms.apply(oversampler, Xy)    # 同等
```

# イラストレーション

完全な基本例とアニメーションは[こちら](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/oversample_smotenc.ipynb)で見つけることができます。より実用的な例は、[チュートリアル](https://juliaai.github.io/Imbalance.jl/dev/examples/)セクションにあり、Google Colabでのコードの実行についても説明しています。

# 参考文献

[1] N. V. Chawla, K. W. Bowyer, L. O.Hall, W. P. Kegelmeyer, “SMOTE: synthetic minority over-sampling technique,” Journal of artificial intelligence research, 321-357, 2002.
