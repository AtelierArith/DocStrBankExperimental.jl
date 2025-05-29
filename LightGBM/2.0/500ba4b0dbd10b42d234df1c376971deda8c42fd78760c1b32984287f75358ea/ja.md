```
fit!(
estimator::LGBMEstimator, 
X::Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}, 
y::Vector{Ty}, 
test::Tuple{Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}, Vector{Ty}}...;
verbosity::Integer = 1,
is_row_major = false,
weights::Vector{Tw} = Float32[],
init_score::Vector{Ti} = Float64[],
group::Vector{Int} = Int[],
truncate_booster::Bool=true,
```

) where {TX<:Real,Ty<:Real,Tw<:Real,Ti<:Real}     fit!(estimator, X, y[, test...]; [verbosity = 1, is*row*major = false])     fit!(estimator, X, y, train*indices[, test*indices...]; [verbosity = 1, is*row*major = false])     fit!(estimator, train*dataset[, test*datasets...]; [verbosity = 1])

`estimator`を特徴データ`X`とラベル`y`でフィットさせ、`test`のX-yペアを検証セットとして使用します。あるいは、Datasetクラスの形式で`train_dataset`と`test_datasets`を使用して`estimator`をフィットさせます。

各検証セットのエントリを持つ辞書を返します。辞書の各エントリは、`estimator`の各検証指標のエントリを持つ別の辞書です。これらのエントリは、各イテレーションでの検証指標の値を保持する配列です。

## 位置引数

  * `estimator::LGBMEstimator`: フィットさせる推定器。
  * そして、いずれか

      * `X::Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}`: 特徴データ。`SparseArrays.SparseMatrixCSC`である可能性があります。

    `X`が`Union{Float, Missing}`型の場合、欠損値は`NaN`に置き換えられます。`X`が`Int`型の場合、`Float64`にキャストした後に欠損値は`NaN`に置き換えられます。

      * `y::Vector{Ty<:Real}`: ラベル。
      * `test::Tuple{Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}, Vector{Ty}}...`: （オプション）検証セットとして使用される`X`と`y`と同じ型のX-yペアのタプルが1つ以上含まれます。`SparseArrays.SparseMatrixCSC`である可能性があり、欠損値を含むことがあります。これらのテストとトレインの間でスパース/密な混合がサポートされています。
  * または

      * `train_dataset::Dataset`: 準備されたトレインデータセット
      * `test_datasets::Vector{Dataset}`: （オプション）準備されたテストデータセット
  * または

      * `train_filepath::String`: トレーニングデータファイルへのパス。
      * `test_filepath::String`: （オプション）テストデータファイルへのパス。

## キーワード引数

  * `verbosity::Integer`: LightGBMの冗長性を制御するキーワード引数。`< 0`は致命的なログのみ、`0`は警告ログを含み、`1`は情報ログを含み、`> 1`はデバッグログを含みます。
  * `is_row_major::Bool`: `X`が行優先かどうかを示すキーワード引数。`true`は行優先を示し、`false`は列優先（Juliaのデフォルト）を示します。トレイン/テスト間で一貫性が必要です。`SparseArrays.SparseMatrixCSC`や`Dataset`コンストラクタには適用されません。
  * `weights::Vector{Tw<:Real}`: トレーニングウェイト。
  * `init_score::Vector{Ti<:Real}`: 初期スコア。
  * `group::Vector{Int}`: ランキングタスクのためのグループサイズ情報。
  * `truncate_booster::Bool`: 影響の少ない木を削除することでモデルのサイズを縮小できるようにします。デフォルトは`true`です。
