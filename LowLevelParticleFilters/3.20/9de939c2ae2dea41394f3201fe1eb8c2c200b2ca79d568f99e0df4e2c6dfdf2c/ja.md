```
UnscentedKalmanFilter(dynamics, measurement, R1, R2, d0=MvNormal(Matrix(R1)); p = NullParameters(), ny, nu, weight_params)
UnscentedKalmanFilter{IPD,IPM,AUGD,AUGM}(dynamics, measurement_model::AbstractMeasurementModel, R1, d0=SimpleMvNormal(R1); p=NullParameters(), nu, weight_params)
```

不確実性を伝播させる非線形状態推定器で、無香変換を使用します。

ダイナミクスと測定関数は、次のいずれかの形式である必要があります。

```
x' = dynamics(x, u, p, t) + w
y  = measurement(x, u, p, t) + e
```

```
x' = dynamics(x, u, p, t, w)
y  = measurement(x, u, p, t, e)
```

ここで `w ~ N(0, R1)`, `e ~ N(0, R2)` および `x(0) ~ d0` です。前者（デフォルト）は、ノイズが加算的であり、ダイナミクスと測定の更新の*後*に追加されることを仮定しています。一方、後者は、ダイナミクス関数がノイズ項に対応する追加の引数を取ることを仮定しています。後者の形式（時々「拡張形式」と呼ばれる）は、ノイズが乗算的である場合や、ノイズがダイナミクスと測定の更新の*前*に追加される場合に便利です。この形式の使用方法についての詳細は、以下の「拡張UKF」を参照してください。どちらの場合でも、ノイズは離散時間ホワイトノイズとしてモデル化されるべきです。詳細は「離散化: [共分散行列](@ref)」を参照してください。

行列 `R1, R2` は時間変化する可能性があり、例えば `R1[:, :, t]` は時間インデックス `t` における $R_1$ 行列を含みます。また、次の形式の関数として与えることもできます。

```
Rfun(x, u, p, t) -> R
```

最大のパフォーマンスを得るために、StaticArrays.jl から静的サイズの行列を提供してください。

`ny, nu` は出力と入力の数を示します。

# `u` のカスタムタイプ

入力 `u` は、名前付きタプルやカスタム構造体など、任意のタイプである可能性があります。入力データで提供される `u` は、ダイナミクスと測定関数に直接渡されるため、タイプがダイナミクスと互換性があれば問題ありません。唯一の例外は、`simulate` を呼び出す場合で、これは `u` が配列であることを仮定しています。

# 拡張UKF

ノイズが加算的でない場合、UKFの拡張形式を使用できます。この形式では、ダイナミクス関数がノイズ項に対応する追加の入力引数を取ります。この形式を有効にするために、型付きコンストラクタ

```
UnscentedKalmanFilter{inplace_dynamics,inplace_measurement,augmented_dynamics,augmented_measurement}(...)
```

が使用され、ブール型パラメータは次の意味を持ちます。

  * `inplace_dynamics`: `true` の場合、ダイナミクス関数はインプレースで動作し、すなわち `dynamics(dx, x, u, p, t)` の最初の引数を修正します。デフォルトは `false` です。
  * `inplace_measurement`: `true` の場合、測定関数はインプレースで動作し、すなわち `measurement(y, x, u, p, t)` の最初の引数を修正します。デフォルトは `false` です。
  * `augmented_dynamics`: `true` の場合、ダイナミクス関数は追加のノイズ入力 `w` で拡張されます。すなわち、`dynamics(x, u, p, t, w)` です。デフォルトは `false` です。
  * `augmented_measurement`: `true` の場合、測定関数は追加のノイズ入力 `e` で拡張されます。すなわち、`measurement(x, u, p, t, e)` です。デフォルトは `false` です。（測定ノイズの自由度が測定の数よりも少ない場合、Cholesky因子分解で失敗する可能性があります。詳細は以下の「カスタムCholesky因子分解」を参照してください）。

拡張ダイナミクスの使用は、追加の計算コストを伴います。使用されるシグマ点の数は `2L+1` で、ここで `L` は拡張状態ベクトルの長さです。拡張なしの場合、`L = nx`、拡張ありの場合、ダイナミクスに対しては `L = nx + nw`、測定に対しては `L = nx + ne` です。

# 重みの調整

シグマ点の広がりは `weight_params::UTParams` によって制御されます。チュートリアルについては、[Docs: Unscented transform](https://baggepinnen.github.io/LowLevelParticleFilters.jl/dev/ut/) を参照してください。デフォルトは、重みなしのシグマ点のための [`TrivialParams`](@ref) であり、他のオプションには [`WikiParams`](@ref) と [`MerweParams`](@ref) があります。

# シグマ点の拒否

困難なダイナミクスの問題に対して、ダイナミクス更新後にシグマ点を拒否するためのメカニズムが提供されています。関数 `reject(x) -> Bool` をキーワード引数 `reject` を通じて提供することができ、$x(t+1)$ のシグマ点を拒否すべき場合に `true` を返します。例えば、不安定性や非有限数が検出された場合です。拒否された点は、伝播された平均点（平均点は拒否できません）に置き換えられます。この関数は、UKFのコンストラクタに提供するか、[`predict!`](@ref) 関数に渡すことができます。

# カスタム測定モデル

デフォルトでは、標準の算術平均と `e(y, yh) = y - yh` が平均およびイノベーション関数として使用されます。

明示的に作成された [`UKFMeasurementModel`](@ref) を渡すことで、平均、共分散、およびイノベーションを計算するカスタム関数を提供できます。これは、状態または測定が多様体上に存在する状況で便利です。さらに、キーワード引数 `state_mean` と `state_cov` をコンストラクタに渡すことで、状態シグマ点の平均および共分散関数をオーバーライドできます。

  * `state_mean(xs::AbstractVector{<:AbstractVector}, w::UKFWeights)` は、状態シグマ点のベクトルの重み付き平均を計算します。
  * `state_cov(xs::AbstractVector{<:AbstractVector}, m, w::UKFWeights)` は、最初の引数が状態シグマ点を表し、2番目の引数がそれらの点の重み付き平均を表します。この関数は、重み `w` によって重み付けされた状態シグマ点の共分散行列を返す必要があります。

カスタム測定モデルの設定方法の詳細については、[`UKFMeasurementModel`](@ref) を参照してください。カスタム測定モデルをUKFコンストラクタの2番目の引数として渡してください。

# カスタムCholesky因子分解

UnscentedKalmanFilterは、シグマ点生成に使用する共分散行列のCholesky因子分解を計算するカスタム関数を提供することをサポートしています。

次のいずれかの条件が満たされると、内部Cholesky因子分解で失敗する可能性があります。

  * ダイナミクスノイズまたは測定ノイズの共分散行列（$R_1, R_2$）が特異である
  * 測定が拡張されており、測定ノイズの自由度が測定の数よりも少ない
  * （特定の技術的条件下で）ダイナミクスが拡張されており、ダイナミクスノイズの自由度が状態変数の数よりも少ない。技術的条件は、線形システムの場合に最も理解しやすく、Kalmanゲインに関連するリカッティ方程式が解を持たないことに対応します。これは、ペア $(A, R1)$ が単位円上に制御不可能なモードを持つ場合に発生する可能性があります。例えば、ノイズによって影響を受けない積分モードがある場合です。

エラーメッセージは次のようになります。

```
ERROR: PosDefException: matrix is not positive definite; Factorization failed.
```

そのような状況では、ノイズモデルと共分散行列を再考することをお勧めします。あるいは、キーワード引数 `cholesky!` を通じてUKFコンストラクタにカスタムCholesky因子分解関数を提供することができます。この関数は、シグネチャ `cholesky!(A::AbstractMatrix)::Cholesky` を持つ必要があります。共分散行列が特異であると予想される場合の有用な代替因子分解は `cholesky! = R->cholesky!(Positive, Matrix(R))` であり、「正の」Cholesky因子分解は、ユーザーによって手動でインストールおよびロードされる必要があるPositiveFactorizations.jlパッケージによって提供されます。
