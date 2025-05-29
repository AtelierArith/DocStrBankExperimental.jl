```
tomek_undersample(
    X, y;
    min_ratios = 1.0, force_min_ratios = false,
    rng = default_rng(), try_preserve_type=true
)
```

# 説明

データ内のトメックリンクの一部であるポイントを削除（「クリーン」）することによって、データセットをアンダーサンプリングします。トメックリンクについては[1]を参照してください。

# 位置引数

  * `X`: 各行がデータセットからの観測値である浮動小数点の行列またはテーブル
  * `y`: `X`の観測値に対応するラベル（例：文字列）の抽象ベクトル

# キーワード引数

  * `min_ratios=1.0`: 各クラスのアンダーサンプリングの最大量を制御するパラメータ。このアルゴリズムがデータをクリーンにしてこの条件が違反される場合、クリーンされたポイントの一部がランダムに復活されて条件が満たされます。

      * 浮動小数点数であることができ、この場合、各クラスは少数クラスのサイズに浮動小数点数を掛けたサイズまでアンダーサンプリングされます。デフォルトでは、すべてのクラスは少数クラスのサイズまでアンダーサンプリングされます。
      * 各クラスラベルをそのクラスの浮動小数点最小比率にマッピングする辞書であることができます。
  * `force_min_ratios=false`: `true`の場合、このアルゴリズムがデータをクリーンにして各クラスの比率が`min_ratios`で指定されたものを超える場合、最終的な比率が`min_ratios`に等しくなるようにさらにアンダーサンプリングが行われます。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `AbstractRNG`オブジェクトまたは`Xoshiro`と一緒に使用される`Integer`シードで、Juliaの`VERSION`がそれをサポートしている場合に使用されます。そうでない場合は、MersenneTwisterを使用します。
  * `try_preserve_type::Bool=true`: `true`の場合、関数は入力テーブル（例：`DataFrame`）の型を変更しないように試みます。ただし、一部のテーブルでは成功しない場合があり、その場合、返されるテーブルは列テーブル（ベクトルの名前付きタプル）になります。このパラメータは、入力が行列の場合は無視されます。

# 戻り値

  * `X_under`: アンダーサンプリング後のデータを含む行列またはテーブル（入力`X`が行列またはテーブルであるかによって異なります）
  * `y_under`: `X_under`に対応するラベルの抽象ベクトル

# 例

```julia
using Imbalance

# 各クラスの確率を設定
class_probs = [0.5, 0.2, 0.3]                         
num_rows, num_continuous_feats = 100, 5
# それに応じてテーブルとカテゴリカルベクトルを生成
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                min_sep=0.01, stds=[3.0 3.0 3.0], class_probs, rng=42)   

julia> Imbalance.checkbalance(y; ref="minority")
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (173.7%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (252.6%) 

# トメックアンダーサンプリングを適用
X_under, y_under = tomek_undersample(X, y; min_ratios=1.0, rng=42)

julia> Imbalance.checkbalance(y_under; ref="minority")
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 22 (115.8%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 36 (189.5%)
```

# MLJモデルインターフェース

キーワード引数を`TomekUndersampler`モデルの初期化時に渡し、位置引数`X, y`を`transform`メソッドに渡します。

```julia
using MLJ
TomekUndersampler = @load TomekUndersampler pkg=Imbalance

# モデルをマシンにラップ
undersampler = TomekUndersampler(min_ratios=1.0, rng=42)
mach = machine(undersampler)

# 変換するデータを提供（フィットするものはありません）
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
                                min_sep=0.01, stds=[3.0 3.0 3.0], class_probs, rng=42)   

# TomekUndersamplerモデルを初期化
undersampler = TomekUndersampler(y_ind; min_ratios=1.0, rng=42)
Xy_under = Xy |> undersampler                    
Xy_under, cache = TableTransforms.apply(undersampler, Xy)    # 同等
```

`TableTransforms`の`reapply(undersampler, Xy, cache)`メソッドは、単に`apply(undersample, Xy)`に戻り、`revert(undersampler, Xy, cache)`はサポートされていません。

# イラストレーション

完全な基本例とアニメーションは[こちら](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/undersample_tomek.ipynb)で見つけることができます。より実用的な例は、[チュートリアル](https://juliaai.github.io/Imbalance.jl/dev/examples/)セクションにあり、Google Colabでのコードの実行についても説明しています。

# 参考文献

[1] Ivan Tomek. Two modifications of cnn. IEEE Trans. Systems, Man and Cybernetics, 6:769–772, 1976.
