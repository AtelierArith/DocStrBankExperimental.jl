```julia
test_differentiation(
    backends::Vector{<:ADTypes.AbstractADType};
    ...
) -> Union{Nothing, DataFrames.DataFrame}
test_differentiation(
    backends::Vector{<:ADTypes.AbstractADType},
    scenarios::Vector{<:DifferentiationInterfaceTest.Scenario};
    testset_name,
    correctness,
    type_stability,
    allocations,
    benchmark,
    excluded,
    detailed,
    logging,
    isapprox,
    atol,
    rtol,
    scenario_intact,
    sparsity,
    reprepare,
    ignored_modules,
    function_filter,
    skip_allocations,
    count_calls,
    benchmark_test,
    benchmark_seconds,
    benchmark_aggregation,
    adaptive_batchsize
) -> Union{Nothing, DataFrames.DataFrame}

```

`backends`のリストに対して`scenarios`のリストを適用し、さまざまなテストやベンチマークを実行します。

# 戻り値

この関数は常に`@testset`を作成して実行しますが、その内容は異なる場合があります。

  * `benchmark == :none`の場合、`nothing`を返します。
  * `benchmark != :none`の場合、[`DifferentiationBenchmarkDataRow`](@ref)のフィールドに対応する列を持つベンチマーク結果の`DataFrame`を返します。

# 位置引数

  * `backends::Vector{<:AbstractADType}`: テストするバックエンド
  * `scenarios::Vector{<:Scenario}`: これらのバックエンドをテストするシナリオ。デフォルトでは、標準の一次および二次シナリオのセットが使用され、その内容は公開APIの一部ではなく、予告なしに変更される可能性があります。

# キーワード引数

  * `testset_name=nothing`: テストセットの表示方法

**テストカテゴリ:**

  * `correctness=true`: 各シナリオで指定された理論値と微分結果を比較するかどうか
  * `type_stability=:none`: JET.jlを使用して演算子の型安定性をチェックするかどうか（およびその方法）
  * `allocations=:none`: AllocCheck.jlを使用して演算子内のアロケーションをチェックするかどうか（およびその方法）
  * `benchmark=:none`: Chairmarks.jlを使用して演算子をベンチマークするかどうか（およびその方法）

`type_stability`、`allocations`、および`benchmark`について、可能な値は`:none`、`:prepared`、または`:full`です。各設定は異なるサブセットの呼び出しをテスト/ベンチマークします：

|       kwarg | prepared operator | unprepared operator | preparation |
| -----------:| -----------------:| -------------------:| -----------:|
|     `:none` |                no |                  no |          no |
| `:prepared` |               yes |                  no |          no |
|     `:full` |               yes |                 yes |         yes |

**その他のオプション:**

  * `excluded::Vector{Symbol}`: 除外する演算子のリスト（例: [`FIRST_ORDER`](@ref) または [`SECOND_ORDER`](@ref)）
  * `detailed=false`: 詳細なテストセットを作成するか、簡潔なテストセットを作成するか
  * `logging=false`: 進行状況をログに記録するかどうか

**正確性オプション:**

  * `isapprox=isapprox`: オブジェクトを近似的に比較するために使用される関数、標準のシグネチャは`isapprox(x, y; atol, rtol)`
  * `atol=0`: 正確性テストのための絶対精度（参照出力と比較する際）
  * `rtol=1e-3`: 正確性テストのための相対精度（参照出力と比較する際）
  * `scenario_intact=true`: 演算子が適用された後にシナリオが変更されていないかどうかをチェックするか
  * `sparsity=false`: ヤコビアン/ヘッセ行列のスパースパターンをチェックするかどうか
  * `reprepare::Bool=true`: 準備引数のサイズが間違っている場合にテスト前に準備を変更するかどうか

**型安定性オプション:**

  * `ignored_modules=nothing`: JET.jlが無視すべきモジュールのリスト
  * `function_filter`: JET.jlが無視すべき関数のフィルター（合理的なデフォルトあり）

**ベンチマークオプション:**

  * `count_calls=true`: ベンチマーク中に関数呼び出しもカウントするかどうか
  * `benchmark_test=true`: ベンチマークがエラーを出さない場合に成功するテストを含めるかどうか
  * `benchmark_seconds=1`: 各ベンチマークを実行する時間
  * `benchmark_aggregation=minimum`: サンプル測定を集約するために使用される関数

**バッチサイズオプション**

  * `adaptive_batchsize=true`: 小さな入力でエラーを防ぐために、バックエンドのプリセットバッチサイズ（存在する場合）を制限するかどうか
