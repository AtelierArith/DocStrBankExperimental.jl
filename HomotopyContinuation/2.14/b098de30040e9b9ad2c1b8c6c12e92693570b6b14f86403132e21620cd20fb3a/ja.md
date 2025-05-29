```
monodromy_solve(F, [sols, p]; options..., tracker_options = TrackerOptions())
```

指定されたパラメータと初期解 `sols` を用いて多項式系 `F(x;p)` をモノドロミー技術で解きます。これは、F のパラメータ空間でループを作成して新しい解を見つけるものです。もし `F` のパラメータ `p` が `F` において*線形的に*のみ現れる場合、自動的に*スタートペア* $(x₀, p₀)$ を計算することが可能です。この場合、`sols` と `p` は省略でき、自動生成されたパラメータは [`parameters`](@ref) 関数を用いて [`MonodromyResult`](@ref) から取得できます。

```
monodromy_solve(F, [sols, L]; dim, codim, intrinsic = nothing, options...,
                              tracker_options = TrackerOptions())
```

`L` が `[LinearSubspace`](@ref) であるとき、`[F(x); L(x)] = 0` という多項式系を解きます。`sols` と `L` が提供されていない場合、`dim` または `codim` を提供する必要があります。ここで `(co)dim` は `V(F)` の成分の期待される (co)次元です。`intrinsic` オプションについては [`linear_subspace_homotopy`](@ref) も参照してください。

## オプション

  * `catch_interrupt = true`: `true` の場合、割り込み（例：Ctrl-Cを押すことによって発生する）をキャッチし、部分結果を返します。
  * `check_startsolutions = true`: `true` の場合、`sols` の各エントリに対してニュートンステップを行い、それが有効なスタートソリューションであるかを確認します。有効でない解は除外されます。
  * `compile = mixed`: `true` の場合、評価のために `System`（または `Homotopy`）が直線プログラム（[`CompiledSystem`](@ref) または [`CompiledHomotopy`](@ref)）にコンパイルされます。これによりコンパイルオーバーヘッドが発生します。`false` の場合、生成されたプログラムは単に解釈されます（[`InterpretedSystem`](@ref) または [`InterpretedHomotopy`](@ref)）。これはコンパイル版よりも遅いですが、コンパイルオーバーヘッドは発生しません。
  * `distance = EuclideanNorm()`: [`UniquePoints`](@ref) に使用される距離関数。
  * `loop_finished_callback = always_false`: 計算を終了するためのコールバック。この関数はループが消耗した後、すべての現在の [`PathResult`](@ref) と共に呼び出されます。2つの引数を取ります。計算を停止すべき場合は `true` を返します。
  * `equivalence_classes=true`: これは少なくとも1つの群作用が提供されている場合にのみ適用されます。この場合、提供された群作用によって一方を他方に変換できる場合、同じ同値類にある2つの解を考慮します。同値類ごとに1つの解のみを追跡します。
  * `group_action = nothing`: 1つの解を取り、構成的に他の解を得る方法がある場合に他の解を返す関数。
  * `group_actions = nothing`: 1つ以上の群作用がある場合、これを使用してそれらの適用を連鎖させることができます。たとえば、2つの群作用 `foo` と `bar` がある場合、`group_actions=[foo, bar]` と設定できます。適用ルールの詳細については [`GroupActions`](@ref) を参照してください。
  * `max_loops_no_progress = 5`: 進展なしに生成される最大反復回数（すなわちループ）。
  * `min_solutions`: 停止ヒューリスティックが適用される前の最小解数。デフォルトでは下限は強制されません。
  * `parameter_sampler = independent_normal`: パラメータ `p` を取り、新しいランダムパラメータ `q` を返す関数。デフォルトでは、パラメータベクトルの各エントリは正規分布から独立に引かれます。
  * `permutations = false`: ループによって誘導される置換を追跡するかどうか。
  * `resuse_loops = :all`: 新たに見つかった解のために他のループを再利用する戦略。`:all` は新しい解をすべての他のループに伝播させ、`:random` はランダムなループを選び、`:none` はループを再利用しません。
  * `target_solutions_count`: この数の解に達した場合、計算は停止します。
  * `threading = true`: パス追跡のマルチスレッドを有効にします。注意：一部のCPUは複数のスレッドを使用するとハングします。これを避けるために、REPL用に1つのインタラクティブスレッドと他のタスク用に `n` スレッドでJuliaを実行します（例：`julia -t 8,1` は `n=8` の場合）。
  * `timeout`: 計算が実行される最大秒数。
  * `trace_test = true`: `true` の場合、すべての解が見つかったかを確認するためにトレーステストが実行されます。これは、線形部分空間でモノドロミーが実行される場合にのみ適用されます。詳細については [`trace_test`](@ref) を参照してください。
  * `trace_test_tol = 1e-10`: トレーステストが成功するための許容誤差。トレースは解の数で割られ、トレース*テスト*トルに比較されます。
  * `unique_points_rtol`: [`unique_points`](@ref) の相対許容誤差。
  * `unique_points_atol`: [`unique_points`](@ref) の絶対許容誤差。

```
