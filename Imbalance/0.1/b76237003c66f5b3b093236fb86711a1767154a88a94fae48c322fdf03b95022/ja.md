```
rose(
    X, y; 
    s=1.0, ratios=1.0, rng=default_rng(),
    try_preserve_type=true
)
```

# 説明

`ROSE`（Random Oversampling Examples）アルゴリズムを使用してデータセットをオーバーサンプリングし、クラスの不均衡を修正します [1] に示されているように。

# 位置引数

  * `X`: 各行がデータセットの観測値である浮動小数点の行列またはテーブル
  * `y`: `X` の観測値に対応するラベル（例：文字列）の抽象ベクトル

# キーワード引数

  * `s::float=1.0`: ガウスカーネルの帯域幅を比例的に制御するパラメータ
  * `ratios=1.0`: 各クラスのオーバーサンプリングの量を制御するパラメータ

      * 浮動小数点数であることができ、この場合、各クラスは浮動小数点数の倍のサイズにオーバーサンプリングされます。デフォルトでは、すべてのクラスは多数派クラスのサイズにオーバーサンプリングされます。
      * 各クラスラベルをそのクラスの浮動小数点比率にマッピングする辞書であることができます。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `AbstractRNG` オブジェクトまたは `Integer` シードで、Julia `VERSION` がサポートしている場合は `Xoshiro` とともに使用されます。そうでない場合は、MersenneTwister を使用します。
  * `try_preserve_type::Bool=true`: `true` の場合、関数は入力テーブル（例：`DataFrame`）の型を変更しないように試みます。ただし、一部のテーブルでは成功しない場合があり、その場合、返されるテーブルは列テーブル（ベクトルの名前付きタプル）になります。このパラメータは、入力が行列の場合は無視されます。

# 戻り値

  * `Xover`: 元のデータとオーバーサンプリングによる新しい観測値を含む行列またはテーブル。入力 `X` が行列またはテーブルであるかによって異なります。
  * `yover`: `Xover` に対応するラベルの抽象ベクトル

# 例

```julia
using Imbalance

# 各クラスの確率を設定
class_probs = [0.5, 0.2, 0.3]                         
num_rows, num_continuous_feats = 100, 5
# それに応じてテーブルとカテゴリカルベクトルを生成
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                class_probs, rng=42)  

julia> Imbalance.checkbalance(y)
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (39.6%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (68.8%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 

# ROSEを適用
Xover, yover = rose(X, y; s=0.3, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)

julia> Imbalance.checkbalance(yover)
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 38 (79.2%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 43 (89.6%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 
```

# MLJ モデルインターフェース

キーワード引数を渡して `ROSE` モデルを初期化し、位置引数 `X, y` を `transform` メソッドに渡します。

```julia
using MLJ
ROSE = @load ROSE pkg=Imbalance

# モデルをマシンにラップ
oversampler = ROSE(s=0.3, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
mach = machine(oversampler)

# 変換するデータを提供（フィットするものはありません）
Xover, yover = transform(mach, X, y)
```

この `MLJ` インターフェースについては、MLJ の [モデルブラウザ](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/) からアクセスしてさらに読むことができます。

# TableTransforms インターフェース

このインターフェースは、入力が1つのテーブル `Xy` であり、`y` がその列の1つであることを前提としています。したがって、コンストラクタには整数 `y_ind` を指定して、`y` がどの列であるかを指定する必要があります。他のキーワード引数はその後に続きます。変換を適用する際には、`Xy` のみが提供されます。

```julia
using Imbalance
using Imbalance.TableTransforms

# 不均衡データを生成
num_rows = 200
num_features = 5
y_ind = 3
Xy, _ = generate_imbalanced_data(num_rows, num_features; 
                                 class_probs=[0.5, 0.2, 0.3], insert_y=y_ind, rng=42)

# ROSEモデルを初期化
oversampler = ROSE(y_ind; s=0.3, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
Xyover = Xy |> oversampler                              
# TableTransforms を使用する場合は同等
Xyover, cache = TableTransforms.apply(oversampler, Xy)    # 同等
```

`TableTransforms` の `reapply(oversampler, Xy, cache)` メソッドは単に `apply(oversample, Xy)` に戻り、`revert(oversampler, Xy, cache)` はテーブルからオーバーサンプリングされた観測値を削除することによって変換を元に戻します。

# イラスト

完全な基本例とアニメーションは [こちら](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/oversample_rose.ipynb) で見つけることができます。より実用的な例は [チュートリアル](https://juliaai.github.io/Imbalance.jl/dev/examples/) セクションにあり、Google Colab でのコードの実行についても説明しています。

# 参考文献

[1] G Menardi, N. Torelli, “Training and assessing classification rules with imbalanced data,”  Data Mining and Knowledge Discovery, 28(1), pp.92-122, 2014.
