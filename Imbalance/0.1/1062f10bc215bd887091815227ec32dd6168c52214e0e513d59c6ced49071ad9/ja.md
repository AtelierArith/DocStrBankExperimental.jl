```
smoten(
    X, y;
    k=5, ratios=1.0, rng=default_rng(),
    try_preserve_type=true
)
```

# 説明

`SMOTE-N`（Synthetic Minority Oversampling Techniques-Nominal）アルゴリズムを使用してデータセットをオーバーサンプリングし、クラスの不均衡を修正します[1]。これは、すべての特徴が名義的であるデータセットに対処するための`SMOTE`の変種です。

# 位置引数

  * `X`: 整数の行列または、要素が`Finite`の[scitypes](https://juliaai.github.io/ScientificTypes.jl/)を持つテーブル。つまり、テーブル入力の場合、各列は`OrderedFactor`または`Multiclass`のいずれかの要素[scitype](https://juliaai.github.io/ScientificTypes.jl/)を持つ必要があります。
  * `y`: `X`の観測に対応するラベル（例：文字列）の抽象ベクトル

# キーワード引数

  * `k::Integer=5`: アルゴリズムで考慮する最近傍の数。`0 < k < n`の範囲内である必要があり、ここでnは最小クラスの観測数です。
  * `ratios=1.0`: 各クラスのオーバーサンプリングの量を制御するパラメータ

      * 浮動小数点数であることができ、この場合、各クラスは多数派クラスのサイズに浮動小数点数を掛けたサイズにオーバーサンプリングされます。デフォルトでは、すべてのクラスが多数派クラスのサイズにオーバーサンプリングされます。
      * 各クラスラベルをそのクラスの浮動小数点比率にマッピングする辞書であることができます。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `AbstractRNG`オブジェクトまたは、Julia `VERSION`がサポートしている場合は`Xoshiro`で使用される`Integer`シード。そうでない場合は、MersenneTwisterを使用します。
  * `try_preserve_type::Bool=true`: `true`の場合、関数は入力テーブル（例：`DataFrame`）の型を変更しないように試みます。ただし、一部のテーブルでは成功しない場合があり、その場合、返されるテーブルは列テーブル（ベクトルの名前付きタプル）になります。このパラメータは、入力が行列の場合は無視されます。

# 戻り値

  * `Xover`: 元のデータとオーバーサンプリングによる新しい観測を含む行列またはテーブル。入力`X`が行列またはテーブルのいずれかに応じて異なります。
  * `yover`: `Xover`に対応するラベルの抽象ベクトル

# 例

```julia
using Imbalance
using ScientificTypes

# 各クラスの確率を設定
class_probs = [0.5, 0.2, 0.3]                         
num_rows = 100
num_continuous_feats = 0
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
(Count, Count)

# 有限のscitype（マルチクラスまたは順序因子）に強制変換
X = coerce(X, autotype(X, :few_to_finite))

# SMOTENを適用
Xover, yover = smoten(X, y; k=5, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)

julia> Imbalance.checkbalance(yover)
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 38 (79.2%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 43 (89.6%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 
```

# MLJモデルインターフェース

キーワード引数を指定して`SMOTEN`モデルを初期化し、位置引数`X, y`を`transform`メソッドに渡します。

```julia
using MLJ
SMOTEN = @load SMOTEN pkg=Imbalance

# モデルをマシンにラップ
oversampler = SMOTEN(k=5, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
mach = machine(oversampler)

# 変換するデータを提供（フィットするものはありません）
Xover, yover = transform(mach, X, y)
```

この`MLJ`インターフェースについては、MLJの[モデルブラウザ](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/)からアクセスしてさらに読むことができます。

# TableTransformsインターフェース

このインターフェースは、入力が1つのテーブル`Xy`であり、`y`がその列の1つであることを前提としています。したがって、コンストラクタには整数`y_ind`を指定して、`y`がどの列であるかを指定する必要があります。他のキーワード引数はその後に続きます。変換を適用する際には、`Xy`のみが提供されます。

```julia
using Imbalance
using ScientificTypes
using Imbalance.TableTransforms

# 不均衡データを生成
num_rows = 100
num_continuous_feats = 0
y_ind = 2
# テーブルとカテゴリベクトルを生成
Xy, _ = generate_imbalanced_data(num_rows, num_continuous_feats; insert_y=y_ind,
                                class_probs= [0.5, 0.2, 0.3], num_vals_per_category=[3, 2],
                                 rng=42)  

# テーブルは有限のscitypesのみを持つ必要があります                                
Xy = coerce(Xy, :Column1=>Multiclass, :Column2=>Multiclass, :Column3=>Multiclass)

# SMOTENモデルを初期化
oversampler = SMOTEN(y_ind; k=5, ratios=Dict(1=>1.0, 2=> 0.9, 3=>0.9), rng=42)
Xyover = Xy |> oversampler                               
# TableTransformsが使用される場合は同等
Xyover, cache = TableTransforms.apply(oversampler, Xy)    # 同等
```

`TableTransforms`の`reapply(oversampler, Xy, cache)`メソッドは、単に`apply(oversample, Xy)`に戻り、`revert(oversampler, Xy, cache)`は、テーブルからオーバーサンプリングされた観測を削除することによって変換を元に戻します。

# イラスト

完全な基本例は[こちら](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/oversample_smoten.ipynb)で見つけることができます。より実用的な例は、[チュートリアル](https://juliaai.github.io/Imbalance.jl/dev/examples/)セクションにあり、Google Colabでのコードの実行についても説明しています。

# 参考文献

[1] N. V. Chawla, K. W. Bowyer, L. O.Hall, W. P. Kegelmeyer, “SMOTE: synthetic minority over-sampling technique,” Journal of artificial intelligence research, 321-357, 2002.
