```
subspaceid(
    data::InputOutputData,
    nx = :auto;
    verbose = false,
    r = nx === :auto ? min(length(data) ÷ 20, 50) : nx + 10, # 最大予測ホライズン
    s1 = r, # 過去の出力の数
    s2 = r, # 過去の入力の数
    W = :MOESP,
    zeroD = false,
    stable = true, 
    focus = :prediction,
    svd::F1 = svd!,
    scaleU = true,
    Aestimator::F2 = \,
    Bestimator::F3 = \,
    weights = nothing,
)

サブスペースベースの同定を使用して状態空間モデルを推定します。いくつかの異なるサブスペースベースのアルゴリズムが利用可能で、`W`キーワードを使用して選択できます。オプションは`:MOESP, :CVA, :N4SID, :IVM`です。

参考文献: Ljung, Theory for the user.

外れ値に対する抵抗は、カスタム因子分解アルゴリズムを提供し、内部の最小二乗推定器を置き換えることで改善できます。以下のキーワード引数`svd`、`Aestimator`、`Bestimator`のドキュメントを参照してください。

返されるモデルは`N4SIDStateSpace`型で、システムモデルを含む`sys`フィールドと、カルマンフィルタ用の共分散行列を含みます。

# 引数:

  * `data`: 同定データ [`iddata`](@ref)
  * `nx`: モデルのランク（モデルの次数）
  * `verbose`: 情報を表示しますか？
  * `r`: 予測ホライズン。この値を長くすると、シミュレーションでモデルの性能が向上する可能性がありますが、計算時間が増加します。
  * `s1`: 過去の出力のホライズン
  * `s2`: 過去の入力のホライズン
  * `W`: 重みのタイプ、`：MOESP、：CVA、：N4SID、：IVM`の中から選択
  * `zeroD`: `D`行列をゼロに強制します。
  * `stable`: 固有値反射を使用して不安定なシステムを安定化します。
  * `focus`: `:prediction`または`simulation`
  * `svd`: `svd`に使用する関数。外れ値に対する抵抗のために、`svd`を適用する前にデータ行列を前処理するために`TotalLeastSquares.rpca`を使用することを検討してください。例えば、`svd = A->svd!(rpca(A)[1])`のようにします。
  * `scaleU`: 入力チャネルのエネルギーを同じにするために再スケールします。
  * `Aestimator`: `A,C`を推定するために使用される推定器関数。デフォルトは``、すなわち最小二乗ですが、外れ値に対する抵抗を得るために、[TotalLeastSquares.jl](https://github.com/baggepinnen/TotalLeastSquares.jl/)の`irls、flts、rtls`などのロバスト推定器を使用できます。
  * `Bestimator`: `B,D`を推定するために使用される推定器関数。重み付き推定は、`weights`キーワード引数とともにTotalLeastSquares.jlの`wls`を渡すことで達成できます。
  * `weights`: `Bestimator`が`wls`の場合、重みのベクトルを提供できます。

# 拡張ヘルプ

より正確な予測モデルは、[`newpem`](@ref)を使用することで得られる場合があります。これは、閉ループデータに対してもバイアスがありません（`subspaceid`は閉ループデータに対してバイアスがあります。ドキュメントの例を参照してください）。予測誤差法は反復的であり、一般的に`subspaceid`よりも高コストであり、最適化の初期推定を形成するためにこの関数（デフォルトで）を使用します。
```
