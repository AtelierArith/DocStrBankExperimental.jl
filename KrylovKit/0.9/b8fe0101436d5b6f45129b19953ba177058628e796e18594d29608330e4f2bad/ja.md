```
eigsolve(A::AbstractMatrix, [x₀, howmany = 1, which = :LM, T = eltype(A)]; kwargs...)
eigsolve(f, n::Int, [howmany = 1, which = :LM, T = Float64]; kwargs...)
eigsolve(f, x₀, [howmany = 1, which = :LM]; kwargs...)
# expert version:
eigsolve(f, x₀, howmany, which, algorithm; alg_rrule=...)
```

行列 `A` にエンコードされた線形マップまたは関数 `f` から、少なくとも `howmany` の固有値を計算します。固有値、固有ベクトル、および `ConvergenceInfo` 構造体を返します。

### 引数:

線形マップは `AbstractMatrix`（密または疎）または一般的な関数または呼び出し可能オブジェクトであることができます。`AbstractMatrix` が使用される場合、初期ベクトル `x₀` を提供する必要はなく、`rand(T, size(A, 1))` として選択されます。線形マップがより一般的に呼び出し可能な関数またはメソッドとしてエンコードされている場合、明示的な初期推測 `x₀` を提供するのが最良のアプローチです。`x₀` は `AbstractVector` 型である必要はなく、ベクトルとして振る舞い、必要なメソッドをサポートする任意の型が受け入れられます（KrylovKit ドキュメントを参照）。代わりに整数 `n` が指定された場合、`x₀` は通常のベクトルであると見なされ、`rand(T, n)` で初期化されます。ここで、`T` のデフォルト値は `Float64` ですが、異なる値が指定されていない限りです。

次の引数はオプションですが、通常は指定する必要があります。`howmany` は計算すべき固有値の数を指定します。`which` はターゲットとする固有値を指定します。`which` の有効な指定は次の通りです。

  * `:LM`: 最大の絶対値を持つ固有値
  * `:LR`: 最大の（最も正の）実部を持つ固有値
  * `:SR`: 最小の（最も負の）実部を持つ固有値
  * `:LI`: 最大の（最も正の）虚部を持つ固有値（`T <: Complex` の場合のみ）
  * `:SI`: 最小の（最も負の）虚部を持つ固有値（`T <: Complex` の場合のみ）
  * [`EigSorter(f; rev = false)`](@ref): `f(λ)` によってソートされたときに最初（または `rev == true` の場合は最後）に現れる固有値 `λ`

!!! note "固有値 `which` の選択に関する注意"
    Krylov メソッドは、線形マップのスペクトルの周辺にある極値固有値に対してうまく機能します。`which` の有効なすべての `Symbol` はこの特性を持っていますが、`EigSorter` を使用して指定することもできます。たとえば、`:LM` は `Eigsorter(abs; rev = true)` と同等です。最小の絶対値のソートは、`EigSorter(abs; rev = false)` を使用して得られますが、（シフトおよび）逆転が使用されないため、固有値がゼロに近い場合は、スペクトルの周辺にも近いことがわかっている場合にのみ成功します。


!!! warning "重複した固有値"
    理論的な観点から、Krylov メソッドはターゲットとする固有値に関連付けられた単一の固有ベクトルしか見つけることができません。重複した固有値の場合、返される特定の固有ベクトルは初期ベクトル `x₀` によって決まります。大規模な問題では、数値ノイズから生成される2つ目の線形独立な固有ベクトルが生成されることが多いため、実際にはあまり問題になりませんが、この潜在的に脆弱な動作に依存しないようにすることが重要です。特に小さな問題に対しては注意が必要です。


引数 `T` は、計算が行われるべき `Number` 型のヒントとして機能しますが、制限はありません。線形マップが自動的に複素値を生成する場合、`T<:Real` が指定されていても複素算術が使用されます。ただし、線形マップと初期推測が実数の場合、部分シュア分解を使用して近似固有値が検索されます。これは、複素共役の固有値がペアで現れ、分割できないことを意味します。そのため、`λ` と `conj(λ)` を異なる方法で扱うように `which` を選択することは違法です。すなわち、`:LI` と `:SI` は無効であり、`by(λ) != by(conj(λ))` につながる任意の `EigSorter` も無効です。

### 戻り値:

戻り値は常に `vals, vecs, info = eigsolve(...)` の形式であり、

  * `vals`: 固有値を含む `Vector` で、長さは少なくとも `howmany` ですが、同じコストで収束した固有値が多い場合はそれ以上になることがあります。固有値は [`Lanczos`](@ref) が使用された場合は実数になり、[`Arnoldi`](@ref) が使用された場合は複素数になります（以下を参照）。
  * `vecs`: `vals` と同じ長さの対応する固有ベクトルの `Vector` です。固有ベクトルは行列として返されず、線形マップがベクトルのような振る舞いをする任意のカスタム Julia 型に作用する可能性があるためです。すなわち、リスト `vecs` の要素は、初期推測 `x₀` に似たオブジェクトであり、異なる `eltype` を持つ可能性があります。特に一般的な行列（すなわち `Arnoldi` を使用する場合）では、固有ベクトルは一般に複素数であり、常に複素数形式で返されます。線形マップが単純な `AbstractMatrix` の場合、`vecs` は `Vector{Vector{<:Number}}` になります。
  * `info`: 次のフィールドを持つ [`ConvergenceInfo`] のオブジェクトです。

      * `info.converged::Int`: 指定された許容誤差 `tol` に実際に収束した固有値と固有ベクトルの数を示します（以下のキーワード引数を参照）。
      * `info.residual::Vector`: `vals` と同じ長さのリストで、残差 `info.residual[i] = f(vecs[i]) - vals[i] * vecs[i]` を含みます。
      * `info.normres::Vector{<:Real}`: `vals` と同じ長さのリストで、残差のノルム `info.normres[i] = norm(info.residual[i])` を含みます。
      * `info.numops::Int`: 線形マップが適用された回数、すなわち `f` が呼び出された回数、またはベクトルが `A` と乗算された回数です。
      * `info.numiter::Int`: Krylov 部分空間が再起動された回数（以下を参照）。

!!! warning "収束の確認"
    要求されたすべての固有値が収束しなかった場合、警告は表示されないため、常に `info.converged >= howmany` を確認してください。


### キーワード引数:

キーワード引数とそのデフォルト値は次の通りです。

  * `verbosity::Int = 0`: 冗長性レベル、すなわち 

      * 0（すべてのメッセージを抑制）
      * 1（警告のみ）
      * 2（最後に収束情報を含む1つのメッセージ）
      * 3（各イテレーションの後に進捗情報）
      * 4+（上記すべてと Lanczos または Arnoldi イテレーションに関する追加情報）
  * `tol::Real`: 要求される精度（シュアベクトルの残差の2ノルムに対応し、固有ベクトルには対応しません）。たとえば、単精度（`Float32`）で作業する場合、デフォルト値を変更する必要があります。
  * `krylovdim::Integer`: 構築される Krylov 部分空間の最大次元。ベクトル空間の次元は知られていないか、チェックされないことに注意してください。たとえば、`x₀` は必ずしも `Base.length` 関数をサポートする必要はありません。実際の問題の次元がデフォルト値よりも小さいことがわかっている場合、`krylovdim` の値を減らすことが有用ですが、原則としてこれは検出されるべきです。
  * `maxiter::Integer`: Krylov 部分空間を再構築できる回数。アルゴリズムの詳細については以下を参照してください。
  * `orth::Orthogonalizer`: 使用される直交化メソッド、[`Orthogonalizer`](@ref) を参照してください。
  * `issymmetric::Bool`: 線形マップが対称である場合、`T<:Real` の場合にのみ意味があります。
  * `ishermitian::Bool`: 線形マップがエルミートである場合。
  * `eager::Bool = false`: 真の場合、Krylov 部分空間の各拡張後に固有値またはシュア分解を積極的に計算して収束をテストします。そうでない場合、Krylov 部分空間の次元が `krylovdim` になるまで待ちます。これは、初期推測が非常に良い場合に、より早く戻ることができますが、密なシュア分解を多く計算する必要があるため、オーバーヘッドもあります。

デフォルト値は `tol = KrylovDefaults.tol`、`krylovdim = KrylovDefaults.krylovdim`、`maxiter = KrylovDefaults.maxiter`、`orth = KrylovDefaults.orth` であり、詳細は [`KrylovDefaults`](@ref) を参照してください。

最後の2つのパラメータのデフォルト値はメソッドによって異なります。`AbstractMatrix` が使用される場合、`issymmetric` と `ishermitian` はその行列に対してチェックされます。それ以外の場合、デフォルト値は `issymmetric = false` および `ishermitian = T <: Real && issymmetric` です。キーワード引数の値が提供されると、行列の場合でもチェックは行われません。

最後のキーワード引数 `alg_rrule` は、`eigsolve` が逆モード自動微分が使用される設定で使用される場合にのみ関連します。`eigsolve` のためにカスタム `ChainRulesCore.rrule` が定義されており、`alg_rrule` を介して指定できるさまざまなアルゴリズムを使用して評価できます。適切なデフォルトが選択されるため、このキーワード引数は、このデフォルトの選択が失敗したり、効率的に機能しない場合にのみ使用する必要があります。`alg_rrule` の可能な値と、それが使用されるアルゴリズムに与える影響についての詳細は、ドキュメントを確認してください。

### アルゴリズム

最終的な（専門的な）メソッドは、デフォルト値やキーワード引数なしで呼び出されるものであり、直接使用することもできます。ここでは、アルゴリズムを明示的に [`Lanczos`](@ref)（実対称または複素エルミート問題用）または [`Arnoldi`](@ref)（一般的な問題用）として指定します。これらの名前は Krylov 部分空間を構築するプロセスを指しますが、実際のアルゴリズムは Krylov-Schur アルゴリズムの実装であり、Krylov 部分空間を動的に縮小および拡大することができます。すなわち、再起動は現在の Krylov 部分空間の一部を保持するいわゆる厚い再起動です。

!!! note "収束に関する注意"
    一般的な問題の場合、`Arnoldi` メソッドが使用されると、固有値の収束は固有ベクトルの残差 `norm(f(vecs[i]) - vals[i]*vecs[i])` のノルムに基づくのではなく、対応するシュアベクトルの残差のノルムに基づきます。

    固有ベクトルを計算することに興味がない場合や、直接部分シュア分解を使用したい場合は、[`schursolve`](@ref) を参照してください。実数の算術で完全に作業したい場合（線形マップと初期推測が実数の場合）も同様です。実数の問題のすべての要求された固有値が実数であり、それに関連する固有ベクトルも実数であることがわかっている場合は、[`realeigsolve`](@ref) を使用することもできます。


```
