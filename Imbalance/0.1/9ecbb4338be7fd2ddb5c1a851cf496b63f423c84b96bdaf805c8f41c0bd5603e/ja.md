```
enn_undersample(
    X, y; k = 5, keep_condition = "mode",
    min_ratios = 1.0, force_min_ratios = false,
    rng = default_rng(), try_preserve_type=true
)
```

# 説明

特定の条件（例えば、近隣の大多数と異なるクラスに属すること）に違反するポイントを削除することによってデータセットをアンダーサンプリングします。これは[1]で提案されています。

# 位置引数

  * `X`: 各行がデータセットからの観測値である浮動小数点の行列またはテーブル
  * `y`: `X`の観測値に対応するラベル（例えば、文字列）の抽象ベクトル

# キーワード引数

  * `k::Integer=5`: アルゴリズムで考慮する最近傍の数。`0 < k < n`の範囲内である必要があります。ここで、nはデータの観測値の数です。`n ≤ k`の場合、自動的に`n-1`に設定されます。
  * `keep_condition::AbstractString="mode"`: 違反時にポイントを削除する条件。`"exists"`、`"mode"`、`"only mode"`、`"all"`のいずれかを取ります。

      * `"exists"`: ポイントには同じクラスの近隣が少なくとも1つ存在する
      * `"mode"`: ポイントのクラスは近隣の最も頻繁なクラスの1つである（多く存在する可能性がある）
      * `"only mode"`: ポイントのクラスは近隣の中で唯一の最も頻繁なクラスである
      * `"all"`: ポイントのクラスはすべての近隣と同じである
  * `min_ratios=1.0`: 各クラスに対して行うアンダーサンプリングの最大量を制御するパラメータ。このアルゴリズムがデータをクリーンにする程度がこの条件に違反する場合、クリーンされたポイントの一部がランダムに復活し、条件が満たされるようになります。

      * 浮動小数点数であることができ、この場合、各クラスは少数クラスのサイズに浮動小数点を掛けたサイズまでアンダーサンプリングされます。デフォルトでは、すべてのクラスが少数クラスのサイズにアンダーサンプリングされます。
      * 各クラスラベルをそのクラスの浮動小数点最小比率にマッピングする辞書であることができます。
  * `force_min_ratios=false`: `true`の場合、このアルゴリズムがデータをクリーンにして各クラスの比率が`min_ratios`で指定されたものを超える場合、最終的な比率が`min_ratios`に等しくなるようにさらにアンダーサンプリングが行われます。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `AbstractRNG`オブジェクトまたは、Juliaの`VERSION`がサポートしている場合に`Xoshiro`で使用される`Integer`シード。そうでない場合は、MersenneTwisterを使用します。
  * `try_preserve_type::Bool=true`: `true`の場合、関数は入力テーブル（例えば、`DataFrame`）の型を変更しないように試みます。ただし、一部のテーブルでは成功しない場合があり、その場合、返されるテーブルは列テーブル（ベクトルの名前付きタプル）になります。入力が行列の場合、このパラメータは無視されます。

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

# ennアンダーサンプリングを適用
X_under, y_under = enn_undersample(X, y; k=3, keep_condition="only mode", 
                                   min_ratios=0.5, rng=42)

julia> Imbalance.checkbalance(y_under; ref="minority")
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 10 (100.0%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 10 (100.0%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 24 (240.0%) 
```

# MLJモデルインターフェース

キーワード引数を`ENNUndersampler`モデルの初期化時に渡し、位置引数`X, y`を`transform`メソッドに渡します。

```julia
using MLJ
ENNUndersampler = @load ENNUndersampler pkg=Imbalance

# モデルをマシンにラップ
undersampler = ENNUndersampler(k=3, keep_condition="only mode", min_ratios=0.5, rng=42)
mach = machine(undersampler)

# 変換するデータを提供（フィットする必要はありません）
X_under, y_under = transform(mach, X, y)
```

この`MLJ`インターフェースについては、MLJの[モデルブラウザ](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/)からアクセスしてさらに読むことができます。

# TableTransformsインターフェース

このインターフェースは、入力が1つのテーブル`Xy`であり、`y`がその列の1つであることを前提としています。したがって、コンストラクタには整数`y_ind`を指定して、`y`がどの列であるかを指定する必要があります。変換を適用する際には、`Xy`のみが提供されます。

```julia
using Imbalance
using Imbalance.TableTransforms

# 不均衡データを生成
num_rows = 100
num_features = 5
y_ind = 3
Xy, _ = generate_imbalanced_data(num_rows, num_features; 
                                 min_sep=0.01, stds=[3.0 3.0 3.0], class_probs, rng=42)

# ENNアンダーサンプラーモデルを初期化
undersampler = ENNUndersampler(y_ind; k=3, keep_condition="only mode", rng=42)
Xy_under = Xy |> undersampler                    
Xy_under, cache = TableTransforms.apply(undersampler, Xy)    # 同等
```

`TableTransforms`の`reapply(undersampler, Xy, cache)`メソッドは、単に`apply(undersample, Xy)`に戻り、`revert(undersampler, Xy, cache)`はサポートされていません。

# イラスト

アニメーションを含む完全な基本例は[こちら](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/undersample_enn.ipynb)で見つけることができます。より実用的な例は、[チュートリアル](https://juliaai.github.io/Imbalance.jl/dev/examples/)セクションにあり、Google Colabでのコードの実行についても説明しています。

# 参考文献

[1] Dennis L Wilson. Asymptotic properties of nearest neighbor rules using edited data.  	IEEE Transactions on Systems, Man, and Cybernetics, pages 408–421, 1972.
