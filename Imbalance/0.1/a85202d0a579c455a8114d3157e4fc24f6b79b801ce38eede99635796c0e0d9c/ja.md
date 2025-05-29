```
borderline_smote1(
    X, y;
    m=5, k=5, ratios=1.0, rng=default_rng(),
    try_preserve_type=true, verbosity=1
)
```

# 説明

ボーダーラインSMOTE1アルゴリズムを使用してデータセットをオーバーサンプリングし、クラスの不均衡を修正します [1] に示されているように。

# 位置引数

  * `X`: 各行がデータセットの観測値である浮動小数点数の行列またはテーブル
  * `y`: `X`の観測値に対応するラベル（例：文字列）の抽象ベクトル

# キーワード引数

  * `m::Integer=5`: ボーダーラインSMOTE1条件を確認する際に考慮する近傍の数。`0 < m < N` の範囲内である必要があります。ここで、Nはデータの観測値の数です。`N ≤ m` の場合、自動的に `N-1` に設定されます。
  * `k::Integer=5`: アルゴリズムのSMOTE部分で考慮する最近傍の数。`0 < k < n` の範囲内である必要があります。ここで、nは最小クラスの観測値の数です。`l`ポイントを持つ任意のクラスに対して、`l ≤ k` の場合、自動的に `l-1` に設定されます。
  * `ratios=1.0`: 各クラスのオーバーサンプリングの量を制御するパラメータ

      * 浮動小数点数であることができ、この場合、各クラスは多数派クラスのサイズに浮動小数点数を掛けたサイズにオーバーサンプリングされます。デフォルトでは、すべてのクラスが多数派クラスのサイズにオーバーサンプリングされます。
      * 各クラスラベルをそのクラスの浮動小数点比率にマッピングする辞書であることができます。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `Xoshiro`と一緒に使用するための `AbstractRNG` オブジェクトまたは `Integer` シード。Juliaの `VERSION` がそれをサポートしている場合。そうでない場合は、MersenneTwisterを使用します。
  * `try_preserve_type::Bool=true`: `true` の場合、関数は入力テーブル（例：`DataFrame`）の型を変更しないように試みます。ただし、一部のテーブルでは成功しない場合があり、その場合、返されるテーブルは列テーブル（ベクトルの名前付きタプル）になります。このパラメータは、入力が行列の場合は無視されます。
  * `verbosity::Integer=1`: `0` より大きい場合、オーバーサンプリングに参加するポイントに関する情報がログに記録されます。

# 戻り値

  * `Xover`: 元のデータとオーバーサンプリングによって生成された新しい観測値を含む行列またはテーブル。入力 `X` が行列またはテーブルであるかどうかに応じて。
  * `yover`: `Xover` に対応するラベルの抽象ベクトル。

# 例

```julia
using Imbalance

# 各クラスの確率を設定
class_probs = [0.5, 0.2, 0.3]                         
num_rows, num_continuous_feats = 1000, 5
# それに応じてテーブルとカテゴリカルベクトルを生成
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                stds=[0.1 0.1 0.1], min_sep=0.01, class_probs, rng=42)            

julia> Imbalance.checkbalance(y)
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 200 (40.8%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 310 (63.3%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 490 (100.0%) 

# ボーダーラインSMOTE1を適用
Xover, yover = borderline_smote1(X, y; m = 3, 
               k = 5, ratios = Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng = 42)

julia> Imbalance.checkbalance(yover)
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 392 (80.0%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 441 (90.0%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 490 (100.0%) 
```

# MLJモデルインターフェース

キーワード引数を使用して `BorderlineSMOTE1` モデルを初期化し、位置引数 `X, y` を `transform` メソッドに渡します。

```julia
using MLJ
BorderlineSMOTE1 = @load BorderlineSMOTE1 pkg=Imbalance

# モデルをマシンにラップ
oversampler = BorderlineSMOTE1(m=3, k=5, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
mach = machine(oversampler)

# 変換するデータを提供（フィットするものはありません）
Xover, yover = transform(mach, X, y)
```

この `MLJ` インターフェースについては、MLJの [モデルブラウザ](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/) からアクセスしてさらに読むことができます。

# TableTransformsインターフェース

このインターフェースは、入力が1つのテーブル `Xy` であり、`y` がその列の1つであることを前提としています。したがって、コンストラクタには整数 `y_ind` を指定して、`y` がどの列であるかを指定する必要があります。他のキーワード引数はその後に続きます。変換を適用する際には、`Xy` のみが提供されます。

```julia
using Imbalance
using Imbalance.TableTransforms

# 不均衡データを生成
num_rows = 1000
num_features = 5
y_ind = 3
Xy, _ = generate_imbalanced_data(num_rows, num_features; 
                                 class_probs=[0.5, 0.2, 0.3], min_sep=0.01, insert_y=y_ind, rng=42)

# ボーダーラインSMOTE1オーバーサンプリングモデルを初期化
oversampler = BorderlineSMOTE1(y_ind; m=3, k=5, 
              ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
Xyover = Xy |> oversampler                              
# TableTransformsが使用される場合は同等
Xyover, cache = TableTransforms.apply(oversampler, Xy)    
```

`TableTransforms` の `reapply(oversampler, Xy, cache)` メソッドは、単に `apply(oversample, Xy)` に戻り、`revert(oversampler, Xy, cache)` はオーバーサンプリングされた観測値をテーブルから削除することによって変換を元に戻します。

# イラスト

完全な基本例とアニメーションは [こちら](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/oversample_smote1_borderline.ipynb) で見つけることができます。より実用的な例は、[チュートリアル](https://juliaai.github.io/Imbalance.jl/dev/examples/) セクションにあり、Google Colabでのコードの実行についても説明しています。

# 参考文献

[1] Han, H., Wang, W.-Y., & Mao, B.-H. (2005). Borderline-SMOTE: A new over-sampling method in imbalanced data sets learning.      In D.S. Huang, X.-P. Zhang, & G.-B. Huang (Eds.), Advances in Intelligent Computing (pp. 878-887). Springer. 
