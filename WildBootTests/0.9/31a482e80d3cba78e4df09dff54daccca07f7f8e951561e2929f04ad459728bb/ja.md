wildboottest([T::DataType=Float64,] R::AbstractMatrix, r::AbstractVector;               resp, <optional keyword arguments>) -> WildBootTests.BootTestResult

ワイルドブートストラップに基づく仮説検定を実行する関数

# 位置引数

  * `T::DataType`: 入力、結果、および計算のデータ型: Float32 または Float64 (デフォルト)
  * `R::AbstractMatrix` と `r::AbstractVector`: 帰無仮説 Rβ=r を表す必要な行列とベクトル; 下記の注意を参照

# 必要なキーワード引数

  * `resp::AbstractVector`: 応答/従属変数 (y または Roodman et al. (2019) の y₁)

# オプションのキーワード引数

  * `predexog::AbstractVecOrMat`: 外生的予測因子、定数項を含む場合 (X/X₁)
  * `predendog::AbstractVecOrMat`: 内生的予測因子 (Y₂)
  * `inst::AbstractVecOrMat`: 楽器 (X₂)
  * `R1::AbstractMatrix` と `r1::AbstractVector`: モデル制約; `R` と `r` と同じ形式
  * `clustid::AbstractVecOrMat{<:Integer}`: エラーおよびブートストラップクラスタ識別子のデータベクトル/行列; 注意を参照
  * `nbootclustvar::Integer=size(clustid,2)`: ブートストラップクラスタリング変数の数
  * `nerrclustvar::Integer=nbootclustvar`: エラークラスタリング変数の数
  * `issorted:Bool=false`: 時間節約フラグ: データ行列はすでに列タイプ 2、次に 3、次に 1 でソートされている (注意を参照)
  * `hetrobust::Bool=true`: エラーが iid として扱われない限り true
  * `feid::AbstractVector{<:Integer}`: 一方向固定効果グループ識別子のデータベクトル
  * `fedfadj::Integer`: 固定効果が消費する自由度; デフォルトは固定効果の数
  * `obswt::AbstractVector=[]`: 観測重みベクトル; デフォルトは等重み
  * `fweights::Bool=false`: 周波数重みの場合は true
  * `maxmatsize::Number`: 補助重み行列 (v) の最大サイズ、ギガバイト単位
  * `ptype::Symbol=:symmetric`: p 値のタイプ (`:symmetric`, `:equaltail`, `:lower`, `:upper`)
  * `bootstrapc::Bool=false`: bootstrap-t の代わりに bootstrap-c を要求する場合は true
  * `liml::Bool=false`: LIML または Fuller LIML の場合は true
  * `fuller::Number`: Fuller LIML ファクター
  * `kappa::Number`: *k*-クラス推定の固定 κ
  * `arubin::Bool=false`: Anderson-Rubin テストの場合は true
  * `small::Bool=true`: G/(G-1) × N/(N-k) でテスト統計量を乗算する場合は true、ここで G, N, k はクラスタ、観測、予測因子の数
  * `clusteradj::Bool=true`: G/(G-1) ファクターを削除する場合は false
  * `clustermin::Bool=false``: 多方向クラスタリングの場合、すべてのクラスタリングに対して最小の G に基づく G/(G-1) ファクターを使用する場合は true
  * `jk::Bool=false`: ブートストラップクラスタによってジャックナイフされた残差に基づいてブートストラップデータ生成プロセスを基にする場合は true
  * `scorebs::Bool=false`: ワイルドブートストラップの代わりにスコアブートストラップの場合は true
  * `reps::Integer=999`: ブートストラップの反復回数; `reps` = 0 は `imposenull` = `true` (または `false`) の場合に古典的な Rao (または Wald) テストを要求
  * `imposenull::Bool=true`: 帰無仮説を課す場合は true
  * `auxwttype::Symbol=:rademacher`: 補助重みのタイプ (`:rademacher`, `:mammen`, `:webb`, `:normal`, `:gamma`)
  * `rng::AbstractRNG=MersenneTwister()`: 擬似乱数生成器
  * `level::Number=.95`: 有意水準 (0-1)
  * `rtol::Number=1e-3`: 信頼区間の境界決定のための許容誤差
  * `madjtype::Symbol=:none`: 多重仮説調整 (`:none`, `:bonferroni`, `:sidak`)
  * `nH0::Integer=1`: テストされる仮説の数、現在テストされているものを含む
  * `ml::Bool=false`: (非線形) ML 推定の場合は true
  * `scores::AbstractVecOrMat`: ML のための事前計算されたスコア
  * `beta::AbstractVector`: ML のためのパラメータ推定
  * `A::AbstractMatrix`: ML のための共分散推定
  * `gridmin`: グラフの下限のベクトル; 最大長 2、`missing`/`NaN` エントリは wildboottest() に選択を依頼
  * `gridmax`: グラフの上限のベクトル; `missing`/`NaN` エントリは wildboottest() に選択を依頼
  * `gridpoints`: サンプリングポイントの数のベクトル; `missing`/`NaN` エントリは wildboottest() に選択を依頼
  * `getdist::Bool=:false`: t/z/F/χ² 統計のブートストラップ分布を返すかどうか; およびその分子
  * `getci::Bool=true`: 信頼区間を返すかどうか
  * `getplot::Bool=getci`: プロットデータを生成するかどうか
  * `getauxweights::Bool=false`: 補助重み行列 (v) を保存するかどうか

# 注意

`T`、`ptype`、`auxwttype`、および `madjtype` は文字列でも可能です。例: `"Float32"` および `"webb"`。

帰無仮説の記述における `R` の列は、行列 [`predexog` `predendog`] の列に対応する必要があります。ここで、`predendog` は楽器を持つ回帰においてのみ非空です。

`clustid` の列を次のように並べます:

1. ブートストラップクラスタを定義するためにのみ使用される変数、サブクラスターブートストラップのように。
2. ブートストラップクラスタとエラークラスタの両方を定義するために使用される変数。
3. エラークラスタを定義するためにのみ使用される変数。

`nbootclustvar` はタイプ 1 または 2 の列の数であり、`nerrclustvar` はタイプ 2 または 3 の列の数です。通常、`clustid` はタイプ 2 の単一列であり、`nbootclustvar` と `nerrclustvar` はデフォルトで 1 です。

`wildboottest()` は欠損データ値を処理しません: すべてのデータおよび識別子行列は推定サンプルに制限される必要があります。
