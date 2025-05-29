```
geneigsolve((A::AbstractMatrix, B::AbstractMatrix), [howmany = 1, which = :LM,
                                T = promote_type(eltype(A), eltype(B))]; kwargs...)
geneigsolve(f, n::Int, [howmany = 1, which = :LM, T = Float64]; kwargs...)
geneigsolve(f, x₀, [howmany = 1, which = :LM]; kwargs...)
# expert version:
geneigsolve(f, x₀, howmany, which, algorithm)
```

少なくとも `howmany` 個の一般化固有値 $λ$ と一般化固有ベクトル $x$ を計算します。これらは $(A - λB)x = 0$ の形をしており、`A` と `B` は `AbstractMatrix` のインスタンスであるか、行列ベクトル積を実装する関数のいずれかです。関数が使用される場合、`A` と `B` の作用を2つの関数のタプル（または関数と `AbstractMatrix`）を介して指定するか、単一の引数 `x` を取り、`A*x` と `B*x` に対応する2つの結果を返す単一の関数を使用することができます。計算された固有値、固有ベクトル、および `ConvergenceInfo` 構造体を返します。

### 引数:

最初の引数は、2つの線形写像のタプルであるか、どちらかの関数または `AbstractMatrix` であり、`A` と `B` の作用を表します。あるいは、単一の引数 `x` を取り、結果として `(A*x, B*x)` の同等物を返す単一の関数を使用することもできます。この後者の形式は、Julia の `do` ブロック構文と互換性があります。`A` または `B` のいずれかに `AbstractMatrix` が使用される場合、初期ベクトル `x₀` を提供する必要はなく、`A` が `AbstractMatrix` の場合は `rand(T, size(A,1))` として選択されます（または `B` のみが `AbstractMatrix` の場合も同様です）。ここで `T = promote_type(eltype(A), eltype(B))` は、両方の `A` と `B` が `AbstractMatrix` のインスタンスである場合、または単に `AbstractMatrix` であるものの `eltype` です。両方の `A` と `B` が呼び出し可能な関数またはメソッドとしてより一般的にエンコードされている場合、明示的な初期推測 `x₀` を提供するのが最良のアプローチです。`x₀` は `AbstractVector` 型である必要はなく、ベクトルとして振る舞い、必要なメソッドをサポートする任意の型が受け入れられます（KrylovKit ドキュメントを参照）。`x₀` の代わりに整数 `n` が指定された場合、`x₀` は通常のベクトルであると仮定され、`rand(T,n)` に初期化されます。ここで `T` のデフォルト値は `Float64` ですが、異なる値が指定されない限りです。

次の引数はオプションですが、通常は指定する必要があります。`howmany` は計算すべき固有値の数を指定します。`which` はターゲットとする固有値を指定します。`which` の有効な指定は次の通りです。

  * `:LM`: 最大の絶対値を持つ固有値
  * `:LR`: 最大の（最も正の）実部を持つ固有値
  * `:SR`: 最小の（最も負の）実部を持つ固有値
  * `:LI`: 最大の（最も正の）虚部を持つ固有値（`T <: Complex` の場合のみ）
  * `:SI`: 最小の（最も負の）虚部を持つ固有値（`T <: Complex` の場合のみ）
  * [`EigSorter(f; rev = false)`](@ref): `f(λ)` によってソートされたときに最初（または `rev == true` の場合は最後）に現れる固有値 `λ`

!!! note "固有値 `which` の選択に関する注意"
    Krylov メソッドは、すなわち線形写像のスペクトルの周辺にある極値固有値に対してうまく機能します。`ClosestTo` を使用しても、シフトと反転は行われません。これは、例えば、スペクトルが複素平面の単位円内にあることがわかっていて、固有値を `λ = 1` に最も近い値にターゲットしたい場合に便利です。


引数 `T` は、計算が行われるべき `Number` 型のヒントとして機能しますが、制限的ではありません。線形写像が自動的に複素値を生成する場合、`T<:Real` が指定されていても複素算術が使用されます。

### 戻り値:

戻り値は常に `vals, vecs, info = geneigsolve(...)` の形であり、

  * `vals`: 固有値を含む `Vector` で、長さは少なくとも `howmany` ですが、同じコストで収束した固有値がより多くある場合は長くなる可能性があります。
  * `vecs`: `vals` と同じ長さの対応する固有ベクトルの `Vector`。固有ベクトルは行列として返されず、線形写像がベクトルのような振る舞いを持つ任意のカスタム Julia 型に作用する可能性があるためです。すなわち、リスト `vecs` の要素は、初期推測 `x₀` に通常似たオブジェクトであり、異なる `eltype` を持つ可能性があります。線形写像が単純な `AbstractMatrix` の場合、`vecs` は `Vector{Vector{<:Number}}` になります。
  * `info`: [`ConvergenceInfo`] の型のオブジェクトで、次のフィールドを持ちます。

      * `info.converged::Int`: 指定された許容誤差 `tol` に実際に収束した固有値と固有ベクトルの数を示します（以下のキーワード引数を参照）
      * `info.residual::Vector`: `vals` と同じ長さのリストで、残差 `info.residual[i] = f(vecs[i]) - vals[i] * vecs[i]` を含みます
      * `info.normres::Vector{<:Real}`: `vals` と同じ長さのリストで、残差のノルム `info.normres[i] = norm(info.residual[i])` を含みます
      * `info.numops::Int`: 線形写像が適用された回数、すなわち `f` が呼び出された回数、またはベクトルが `A` で乗算された回数
      * `info.numiter::Int`: Krylov 部分空間が再起動された回数（以下を参照）

!!! warning "収束の確認"
    要求されたすべての固有値が収束しなかった場合、警告は表示されないため、常に `info.converged >= howmany` を確認してください。


### キーワード引数:

キーワード引数とそのデフォルト値は次の通りです。

  * `verbosity::Int = 0`: 冗長性レベル、すなわち 

      * 0（すべてのメッセージを抑制）
      * 1（警告のみ）
      * 2（最後に収束情報のメッセージを1つ）
      * 3（各イテレーション後の進捗情報）
  * `tol::Real`: 要求される精度で、対応する固有ベクトルの2ノルムに対して相対的です。すなわち、`norm((A - λB)x) < tol * norm(x)` の場合に収束が達成されます。固有ベクトルは `dot(x, B*x) = 1` となるように正規化されているため、`norm(x)` は自動的に1ではありません。例えば、単精度（`Float32`）で作業する場合、デフォルト値を変更する必要があります。
  * `krylovdim::Integer`: 構築される Krylov 部分空間の最大次元。ベクトル空間の次元は知られていないか、チェックされないことに注意してください。例えば、`x₀` は必ずしも `Base.length` 関数をサポートする必要はありません。実際の問題の次元がデフォルト値よりも小さいことがわかっている場合、`krylovdim` の値を減らすことが有用ですが、原則としてこれは検出されるべきです。
  * `maxiter::Integer`: Krylov 部分空間を再構築できる回数；アルゴリズムの詳細については以下を参照してください。
  * `orth::Orthogonalizer`: 使用される直交化方法、[`Orthogonalizer`](@ref) を参照
  * `issymmetric::Bool`: 両方の線形写像 `A` と `B` が対称である場合、`T<:Real` の場合にのみ意味があります
  * `ishermitian::Bool`: 両方の線形写像 `A` と `B` がエルミートである場合
  * `isposdef::Bool`: 線形写像 `B` が正定値である場合

デフォルト値は `tol = KrylovDefaults.tol`、`krylovdim = KrylovDefaults.krylovdim`、`maxiter = KrylovDefaults.maxiter`、`orth = KrylovDefaults.orth` によって与えられます；詳細については [`KrylovDefaults`](@ref) を参照してください。

最後の3つのパラメータのデフォルト値はメソッドによって異なります。`AbstractMatrix` が使用される場合、`issymmetric`、`ishermitian` および `isposdef` はその行列に対してチェックされます。そうでない場合、デフォルト値は `issymmetric = false` および `ishermitian = T <: Real && issymmetric` です。値が提供されると、行列の場合でもチェックは行われません。

### アルゴリズム

最後のメソッドは、デフォルト値やキーワード引数なしで呼び出され、直接使用することもできます。ここでアルゴリズムが指定されますが、現在利用可能なのは [`GolubYe`](@ref) のみです。Golub-Ye アルゴリズムは、正定値の `B` を持つエルミート（対称）一般化固有値問題 `A x = λ B x` を解くためのアルゴリズムで、`B` を反転する必要がありません。これは、推定値 `x` から始まるサイズ `krylovdim` の Krylov 部分空間を構築し、`(A - ρ(x) B)` で作用させ、`ρ(x) = dot(x, A*x)/ dot(x, B*x)` を使用し、Lanczos アルゴリズムを採用します。このプロセスは最大 `maxiter` 回繰り返されます。各イテレーション `k>1` では、部分空間は $x_k - x_{k-1}$ を追加することによってサイズ `krylovdim+1` に拡張され、これは Money と Ye によって提案された LOPCG 補正として知られています。`krylovdim = 2` の場合、このアルゴリズムは `LOPCG` と同等になります。

!!! warning "対称定義された一般化固有値問題への制限"
    現在のところ唯一のアルゴリズムは、正定値の `B` を持つ対称/エルミート一般化固有値問題に制限されており、これはキーワード引数 `issymmetric` または `ishermitian` および `isposdef` のデフォルト値には反映されていません。このアルゴリズムを使用する際の影響を理解するために、これらを真に設定することを確認してください。

