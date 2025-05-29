```
Unfold.fit(
    UnfoldDecodingModel,
    design,
    tbl::DataFrame,
    dat::AbstractMatrix,
    model::MLJ.Model,
    target::Pair;
    nfolds = 6,
    eventcolumn = :event,
    unfold_fit_options = (;),
    multithreading = true,
)

`UnfoldDecodingModel`を使用して、重複補正をクロスバリデーション方式で適用し、結果のデータに対してデコーディングを行います。

# 引数

  * `design::`: Unfoldデザインベクター、例: `["eventA"=>(@formula(y~1+condition),firbasis((-0.1,1),100)]`
  * `tbl::DataFrame`: 通常のUnfoldモデルにおけるイベント
  * `data::AbstractMatrix`: 連続EEGデータ、ch x time
  * `model::MLJModelInterface.Probabilistic`: デフォルトではLDA()が使用されますが、他のMLJマシンも可能です
  * `target::Pair`: イベントタイプ->カラム、StringまたはSymbolのペアで、どのイベントと`tbl[:,column]`がデコード対象であるかを示します。例: `"eventA" => :condition`

# キーワード引数

  * `nfolds::Int = 6`: クロスバリデーションのフォールド数
  * `eventcolumn::Union{Symbol,String} = :event` - `tbl`内のカラムで、`design`で定義された基底関数を区別します
  * `unfold_fit_options`: 初期の「重複クリーニング」`Unfold.fit`関数に提供されるオプションの`NamedTuple`引数、例: `unfold_fit_options = (;solver=(x,y)->solver_krylov(x,y,GPU=true))`（GPUフィットのために`Krylov`と`CUDA`を事前にロードする必要があります）
  * `multithreading::Bool = true`: 時間ポイントに対するマルチスレッドの有効化/無効化

# 戻り値

  * `result::UnfoldDecodingModel` : `coef(result)`などを通じて検査できるUnfold型モデル
```
