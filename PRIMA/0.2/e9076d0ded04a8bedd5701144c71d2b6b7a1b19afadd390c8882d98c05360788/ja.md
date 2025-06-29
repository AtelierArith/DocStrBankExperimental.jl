```
prima(f, x0; kwds...) -> x, info
```

は、制約付き最適化問題をおおよそ解決します：

```
min f(x)    subject to   x ∈ Ω ⊆ ℝⁿ
```

ここで、

```
Ω = { x ∈ ℝⁿ | xl ≤ x ≤ xu, Aₑ⋅x = bₑ, Aᵢ⋅x ≤ bᵢ, cₑ(x) = 0, and cᵢ(x) ≤ 0 }
```

は、M.J.D. パウエルのアルゴリズム COBYLA、LINCOA、BOBYQA、または NEWUOA のいずれかによって解決されます。これは、`Ω` によって設定された制約に依存します。これらのアルゴリズムは、目的関数の線形または二次の局所近似に従って変数が更新される信頼領域法に基づいています。目的関数の導関数は必要ありません。

引数は目的関数 `f` と初期変数 `x0` で、出力時に変更されません。目的関数は `f(x)` として呼び出され、`x` は変数であり、次のシグネチャを実装する必要があります：

```
f(x::Vector{Cdouble})::Real
```

返される結果は、変数 `x` とアルゴリズムによって提供される他の情報を収集した構造体オブジェクト `info` を含む 2 タプル `(x, info)` です。`issuccess(info)` が true の場合、アルゴリズムは成功し、`x` は問題の近似解です。

許可されるキーワードは次のとおりです（`n = length(x)` は変数の数です）：

  * `scale`（デフォルト値 `nothing`）は、`n` の正のスケーリングファクターのベクトルで設定できます。指定された場合、問題はスケーリングされた変数 `u ∈ ℝⁿ` で解決され、`u[i] = x[i]/scale[i]` となります。指定されていない場合、すべての変数に対して `scale[i] = 1` と仮定されます。目的関数、制約（線形および非線形）、および境界は変数で指定されたままです。変数をスケーリングすることは、問題の条件を改善し、スケーリングされた変数 `u` がほぼ同じ大きさを持つようにし、異種の変数や異なる単位に適応するのに役立ちます。
  * `rhobeg`（デフォルト値 `1.0`）は、信頼領域の初期半径です。信頼領域の半径は、スケーリングされた変数のユークリッドノルムによって与えられます（上記のキーワード `scale` を参照）。
  * `rhoend`（デフォルト値 `1.0e-6*rhobeg`）は、スケーリングされた変数でアルゴリズムが収束したかどうかを決定するために使用される信頼領域の最終半径です。
  * `ftarget`（デフォルト値 `-Inf`）は、別の収束設定です。`f(x) ≤ ftarget` となるとすぐにアルゴリズムは停止し、ステータス `PRIMA.FTARGET_ACHIEVED` が返されます。
  * `maxfun`（デフォルト `500*n`）は、アルゴリズムに許可される最大関数評価回数です。`f(x)` への呼び出し回数がこの値を超えると、アルゴリズムは停止し、ステータス `PRIMA.MAXFUN_REACHED` が返されます。
  * `iprint`（デフォルト値 `PRIMA.MSG_NONE`）は、アルゴリズムの冗長性のレベルを設定します。可能な値は `PRIMA.MSG_EXIT`、`PRIMA.MSG_RHO`、または `PRIMA.MSG_FEVL` です。ソフトウェアによって印刷される値は、スケーリングされた変数の値です（上記のキーワード `scale` を参照）。
  * `npt`（デフォルト値 `2n + 1`）は、目的関数の局所的な挙動を近似するために使用される点の数で、`n + 2 ≤ npt ≤ (n + 1)*(n + 2)/2` となります。デフォルト値は M.J.D. パウエルによって推奨されるものに対応しています。
  * `xl` と `xu`（デフォルト `fill(+Inf, n)` と `fill(-Inf, n)`）は、変数の要素ごとの下限および上限です。実行可能な変数は `xl ≤ x ≤ xu` となります（要素ごとに）。
  * `linear_eq`（デフォルト `nothing`）は、線形等式制約 `Aₑ⋅x = bₑ` を課すためにタプル `(Aₑ,bₑ)` として指定できます。
  * `linear_ineq`（デフォルト `nothing`）は、線形不等式制約 `Aᵢ⋅x ≤ bᵢ` を課すためにタプル `(Aᵢ,bᵢ)` として指定できます。
  * `nonlinear_eq`（デフォルト `nothing`）は、非線形等式制約を実装する関数 `c_eq` で指定できます。`c_eq(x) = 0` によって定義されます。返されると、非線形等式制約の値は `info.nl_eq` によって提供され、`c_eq(x)` を呼び出す必要がなくなります。
  * `nonlinear_ineq`（デフォルト `nothing`）は、非線形不等式制約を実装する関数 `c_ineq` で指定できます。`c_ineq(x) ≤ 0` によって定義されます。返されると、非線形不等式制約の値は `info.nl_ineq` によって提供され、`c_ineq(x)` を呼び出す必要がなくなります。

特定のパウエルのアルゴリズムを使用するには、[`PRIMA.cobyla`](@ref)、[`PRIMA.lincoa`](@ref)、[`PRIMA.bobyqa`](@ref)、[`PRIMA.newuoa`](@ref)、または [`PRIMA.uobyqa`](@ref) を参照してください。
