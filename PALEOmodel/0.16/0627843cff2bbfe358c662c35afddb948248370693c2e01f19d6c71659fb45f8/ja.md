```
initialize!(model::PB.Model; kwargs...) -> (initial_state::Vector, modeldata::PB.ModelData)
```

`model`を初期化し、次のものを返します：

  * `initial_state` ベクトル
  * モデル配列を含む `modeldata` 構造体。

# 状態ベクトルの初期化

デフォルト引数を使用すると、`model` の状態変数は、`model` を作成するために使用された `.yaml` 設定ファイルで定義された値に初期化されます。

オプションの `pickup_output` 引数を使用して、初期化元のピックアップデータを持つ `OutputWriter` インスタンスを提供できます。これは、デフォルトの初期化の後に適用されるため、モデル状態変数のサブセットを（再）初期化するために使用できます。

# モデル配列のための `DataType`

デフォルト引数を使用すると、`model` 配列は要素型として `Float64` を使用します。自動微分で使用するために、異なるJulia `DataType` を指定するために `eltype` キーワード引数を使用できます。変数ごとの `DataType` は、`:datatype` 変数属性を使用して `String` 値のタグを指定し、`eltypemap` キーワード引数を組み合わせてタグ名 => `DataType` の `Dict` を提供することで指定できます。

# スレッドセーフ

スレッドセーフなモデルは、`PB.create_model_from_config` を呼び出す前にYAML設定ファイルで `threadsafe=true` グローバルパラメータを設定することによって作成できます（これは、スレッドセーフを維持するためにグローバルアキュムレータ変数の特別な処理を必要とする反応で使用されます）、および `method_barrier` を提供します（依存関係のないグループ間の `ReactionMethod` ディスパッチリストに追加するスレッドバリア）：

```
method_barrier = PB.reaction_method_thread_barrier(
    PALEOmodel.ThreadBarriers.ThreadBarrierAtomic("the barrier"),
    PALEOmodel.ThreadBarriers.wait_barrier
)
```

# キーワードの概要

  * `pickup_output=nothing`: 初期化元のピックアップデータを持つOutputWriter
  * `check_units_opt=:no`: リンクされた変数の単位が一貫しているかを確認する（:noでチェックを無効に、:warnで警告を出して続行、:errorでエラーを出して停止）
  * `eltype::Type=Float64`: モデル配列に使用するデフォルトデータ型
  * `eltypemap=Dict{String, DataType}()`: 変数の :datatype 属性を調べるためのデータ型のDict
  * `method_barrier=nothing`: スレッドセーフなモデルを作成するためにディスパッチリストに追加するスレッドバリア
  * `expect_hostdep_varnames=["global.tforce"]`: 期待される非状態変数ホスト依存変数名
  * `SolverView_all=true`: `modeldata.solver_view_all` を作成するために `true`
  * `create_dispatchlists_all=true`: `modeldata.dispatchlists_all` を作成するために `true`
  * `generated_dispatch=true`: `modeldata.dispatchlists_all` のためにコードを自動生成するために `true`（高速ディスパッチ、遅いコンパイル）
