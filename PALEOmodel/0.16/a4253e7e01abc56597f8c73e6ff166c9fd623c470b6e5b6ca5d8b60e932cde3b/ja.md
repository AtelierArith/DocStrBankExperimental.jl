```
SolverView(model, modeldata, arrays_idx; [verbose=true]) 
SolverView(model, modeldata, cellranges; [verbose=false], [indices_from_cellranges=true])
```

数値ソルバーのためのモデル全体または一部のビューを提供します。

空間位置のサブセットに対する `PALEOboxes.VariableAggregator` を含み、`stateexplicit` (`S_e`)、`statetotal` (`S_t`) および `state` (`S_a`) のサブセットで構成される状態変数 `S_all` を定義します。

微分および代数制約は次のように提供されます：

  * ODE ペアの `stateexplicit` (`S_e`) と `stateexplicit_deriv` (`dS_e/dt`)、ここで `dS_e/dt = F(S_all)` です。
  * 暗黙ODE ペアの `total` (`T`) と `total_deriv` (`dT/dt`)、ここで `dT(S_all)/dt = F(S_all)` です。これは、`dT(S_all)/dt = dT(S_all)/dS_all * dS_all/dt` として、時間微分 `dS_t/dt` を暗黙的に決定します。`total` (`T`) 変数の数は `statetotal` 変数 `S_t` の数と等しくなければなりません。
  * 代数 `constraint`s (`C`)、ここで `C(S_all) = 0` であり、`constraint` 変数 `C` の数は `state` 変数 `S_a` の数と等しくなければなりません。

`total` (`T`) 変数が存在しない場合、またはそれらが `S_e` と `S_t` のみの関数 `T(S_e, S_t)` である場合（`S_a` の関数ではない）、状態変数は微分変数 `S_d`（`stateexplicit` (`S_e`) と `statetotal` (`S_t`) で構成される）と代数変数 `state` (`S_a`) のサブセットに分割できます。

利用可能な数値ソルバーの選択は、モデル構成内の状態変数のタイプに依存します：

  * `stateexplicit` (`S_e`) 変数のみを持つシステムは、ODE ソルバー（例：`PALEOmodel.ODE.integrate` による SciML `ODEProblem` として）で解決できます。
  * 一部の ODE ソルバー（左辺に定数質量行列をサポートするもの）は、制約 `C` を持つシステムも解決できます（例：`PALEOmodel.ODE.integrate` による SciML `ODEProblem` として）。
  * 暗黙の `total` (`T`) 変数を持つシステムを解決するには、Sundials IDA のような DAE ソルバーが必要です（例：`PALEOmodel.ODE.integrateDAE` による SciML `DAEProblem` として）。注意：`total` (`T`) と `constraint` (`C`) 変数の任意の組み合わせは、`PALEOmodel.ODE.integrateDAE` を介して Sundials IDA によってサポートされていません。なぜなら、初期条件を一貫して見つけるために使用される IDA ソルバーオプションは、上記のように微分変数と代数変数に分割することを要求するからです。

オプションのアクセスメソッドは、合成 `statevar` および `statevar_sms` を持つ `ODE/DAE solver` ビューを提供します。ここで：

```
- `statevar` は `stateexplicit`、`statetotal`、および `state` の連結です（[`set_statevar!`](@ref)）。
- `statevar_sms` は `stateexplicit_deriv`、`total_deriv`、`constraints` の連結です（[`get_statevar_sms!`](@ref)）。
```

コンストラクタは、`modeldata` 配列セット `arrays_idx` からモデル全体の [`SolverView`](@ref) を作成するか、`cellranges` のドメインと operatorIDs によって定義されたモデル変数のサブセットのためのものです。

# キーワード

  * `indices_from_cellranges=true`: `cellranges` からのインデックス範囲に制限する場合は true、ドメインを定義するために単に `cellranges` を使用する場合は false

および各ドメインの全体を取得します。

  * `hostdep_all=true`: すべてのドメインからホスト依存の非状態変数を含める場合は true
  * `reallocate_hostdep_eltype=Float64`: `hostdep` 変数を再割り当てするためのデータ型（例：任意の

AD タイプを置き換えるため）。
