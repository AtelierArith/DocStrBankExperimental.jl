```
function dynamic_fullsweep!(sysenv::StateEnvs, solver, swdata::SweepData;
                            kwargs...)
```

`solver`によって動的フルスイープ（左から右、右から左）を実行します。最初のスイープは、`swdata.sweepcount=0`に従って、グローバルサブスペース拡張（以下参照）が実行され、その後、`typeof(sysenv) == StateEnvs{ProjMPO}`の場合は純粋な1サイトスイープが行われ、それ以外の場合はフル2サイトスイープが行われます。各ボンドで、最小固有値が`eigthreshold`未満であるか、特定のハーフスイープでそのボンドのボンド次元が`maxdim`に達している場合、次のハーフスイープでそのボンドに対してシングルサイト更新を行い、そうでない場合は2サイト更新を行います。

#### 引数:

  * `sysenv::StateEnvs`.
  * `solver`: 更新のためのソルバー。利用可能なもの: `eig_solver`および`exp_solver`。
  * `swdata::SweepData`.

#### 名前付き引数とそのデフォルト値:

  * `time_step::Union{Float64, ComplexF64, Nothing} = nothing`: TDVPのための時間ステップ。
  * `normalize::Bool = true`: 更新後に正規化するかどうか。
  * `maxdim::Int = typemax(Int)`: SVD切り捨て後の最大ボンド次元。
  * `mindim::Int = 1`: SVD切り捨て後の最小ボンド次元。
  * `cutoff::Float64 = Float64_threshold()`: SVD切り捨てのためのカットオフ。
  * `svd_alg::String = "divide_and_conquer"`.
  * `noise::Float64 = 0.0`.
  * `reverse_step::Bool = false` if `time_step = nothing`, `true` otherwise.
  * `outputlevel::Int = 1`. `0`の場合は情報を出力せず、`1`の場合は毎フルスイープ後に出力し、`2`の場合は毎更新ステップで出力します。
  * `eigthreshold::Float64 = 1E-12`.
  * `extendat::Union{Nothing, Int} = nothing`: 指定された場合、毎`extendat`スイープでグローバルサブスペース拡張が実行され、`typeof(sysenv) == StateEnvs{ProjMPO}`の場合は純粋な1サイトスイープが行われ、それ以外の場合はフル2サイトスイープが行われます。

#### `solver`のための名前付き引数とそのデフォルト値:

KrylovKit.jlのドキュメントを参照してください。

  * `ishermitian::Bool = true`.
  * `solver_tol::Float64 = 1E-14` if `eig_solver`, `1E-12` if `exp_solver`.
  * `solver_krylovdim::Int = 3` if `eig_solver`, `30` if `exp_solver`.
  * `solver_maxiter::Int = 1` if `eig_solver`, `100` if `exp_solver`.
  * `solver_outputlevel::Int = 0`: KrylovKit.jlの`verbosity`を参照してください。
  * `solver_eager::Bool = false` if `eig_solver`, `true` if `exp_solver`.
  * `solver_check_convergence::Bool = false` if `eig_solver`, `true` if `exp_solver`.

#### グローバルサブスペース拡張のための引数とそのデフォルト値:

  * `extension_krylovdim::Int = 3`: GSEに使用されるKrylovベクトルの数。
  * `extension_applyH_cutoff::Float64 = 0.0`: MPOをMPSに適用するためのカットオフ。
  * `extension_applyH_maxdim::Int = maxlinkdim(psi) + 1`: MPOをMPSに適用するための最大ボンド/リンク次元。
  * `extension_cutoff::Float64 = 1E-10`: GSEにおける基底拡張ステップのためのカットオフ。

#### 戻り値:

  * `::Float64`: エネルギーの変化 ΔE
  * `::Float64`: エントロピーの変化 ΔS

`swdata::SweepData`が更新されます。 ```
