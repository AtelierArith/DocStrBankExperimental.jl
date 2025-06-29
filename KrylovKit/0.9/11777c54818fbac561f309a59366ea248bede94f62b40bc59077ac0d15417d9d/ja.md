```
# エキスパートバージョン:
realeigsolve(f, x₀, howmany, which, algorithm; alg_rrule=algorithm)
```

最初の `howmany` 固有値を計算します（`which` で指定された順序に従って）。これは、行列 `A` にエンコードされた実線形写像から、または関数 `f` によって行われます。これらの固有値（およびそれに関連する固有ベクトル）が実数であることが保証される場合に限ります。最初の `howmany` 固有値の中に複素数の固有値がある場合、エラーが発生します。

固有値、固有ベクトル、および `ConvergenceInfo` 構造体を返します。

!!! note "実線形写像に関する注意"
    関数 `f` は、`f(add(x,y)) = add(f(x), f(y))` および `f(scale(x, α)) = scale(f(x), α)` を満たす場合、実線形写像を実装していると言います。ここで、`x` と `y` はベクトル、`α::Real` はスカラーです。これは、ベクトルが複素数演算を使用して表現されている場合でも可能です。たとえば、写像 `f=x-> x + conj(x)` は、複素数線形ではない実線形写像を表します。なぜなら、複素スカラー `α` に対して `f(scale(x, α)) = scale(f(x), α)` を満たさないからです。複素数線形写像は常に実線形写像であるため、特に実数の固有値を探している場合には、この文脈で使用できます。

    ベクトル `x` と `y` を実ベクトル空間の要素として解釈するために、標準内積は `real(inner(x,y))` に置き換えられます。これは、最初からベクトル `x` と `y` が実数演算を使用して表現されている場合には影響がなく、複素ベクトルもシームレスに使用できるようにします。


### 引数:

線形写像は `AbstractMatrix`（密または疎）または一般的な関数または呼び出し可能オブジェクトであることができます。開始ベクトル `x₀` を提供する必要があります。`x₀` は `AbstractVector` 型である必要はなく、ベクトルとして振る舞い、必要なインターフェースをサポートする任意の型が受け入れられます（KrylovKit ドキュメントを参照）。

引数 `howmany` は、計算すべき固有値の数を指定します。`which` は、ターゲットとする固有値を指定します。実問題に対する `which` の有効な仕様は次のとおりです。

  * `:LM`: 最大の絶対値を持つ固有値
  * `:LR`: 最大の（最も正の）実部を持つ固有値
  * `:SR`: 最小の（最も負の）実部を持つ固有値
  * [`EigSorter(f; rev = false)`](@ref): `f(λ)` によってソートされたときに最初（または `rev == true` の場合は最後）に現れる固有値 `λ`

!!! note "固有値 `which` の選択に関する注意"
    Krylov 法は、すなわち線形写像のスペクトルの周辺にある固有値に対してうまく機能します。`which` のすべての有効な `Symbol` はこの特性を持っていますが、`EigSorter` を使用して指定することもできます。たとえば、`:LM` は `Eigsorter(abs; rev = true)` と同等です。最小の絶対値のソートは、たとえば `EigSorter(abs; rev = false)` を使用して得られますが、（シフトおよび）反転が使用されないため、固有値がゼロに近い場合は、スペクトルの周辺に近いことがわかっている場合にのみ成功します。


!!! warning "重複した固有値"
    理論的な観点から、Krylov 法はターゲットとする固有値に関連付けられた単一の固有ベクトルしか見つけることができません。重複した固有値の場合、返される特定の固有ベクトルは開始ベクトル `x₀` によって決まります。大規模な問題では、数値ノイズから生成される2つ目の線形独立な固有ベクトルが、Lanczos または Arnoldi 反復の直交化ステップの結果として生成されることが多いため、実際にはあまり問題になりません。それでも、これは考慮に入れることが重要であり、特に小さな問題に対しては、この潜在的に脆弱な動作に依存しないようにすることが重要です。


引数 `algorithm` は現在、[`Arnoldi`](@ref) のインスタンスのみをサポートしており、ここで Krylov 法のパラメータ（Krylov 次元や最大反復回数など）を指定できます。`realeigsolve` は `eigsolve` よりも一般的に使用されないため、このエキスパートモードの呼び出し構文のみをサポートしており、便利なキーワードインターフェースは現在利用できません。

キーワード引数 `alg_rrule` は、逆モード自動微分の文脈で `realeigsolve` の `pullback` を計算するために使用されるアルゴリズムを指定するために使用できます。

### 戻り値:

戻り値は常に `vals, vecs, info = eigsolve(...)` の形式であり、次のようになります。

  * `vals`: 固有値を含む `Vector` で、長さは少なくとも `howmany` ですが、同じコストで収束した固有値がさらに多い場合は長くなる可能性があります。固有値は実数であり、線形写像の最初の `howmany` 固有値がすべて実数でない場合、`ArgumentError` が発生します。
  * `vecs`: `vals` と同じ長さの対応する固有ベクトルの `Vector` です。固有ベクトルは行列として返されず、線形写像はベクトルのような振る舞いを持つ任意のカスタム Julia 型に作用する可能性があるため、リスト `vecs` の要素は通常、開始推測 `x₀` に似たオブジェクトです。実数の固有値を持つ実問題の場合、固有ベクトルも実数であり、どこでも複素数演算は使用されません。
  * `info`: 次のフィールドを持つ [`ConvergenceInfo`] 型のオブジェクトです。

      * `info.converged::Int`: 実際に指定された許容誤差 `tol` に収束した固有値と固有ベクトルの数を示します（キーワード引数の下で参照）。
      * `info.residual::Vector`: 同じ長さのリストで、残差 `info.residual[i] = f(vecs[i]) - vals[i] * vecs[i]` を含みます。
      * `info.normres::Vector{<:Real}`: 同じ長さのリストで、残差のノルム `info.normres[i] = norm(info.residual[i])` を含みます。
      * `info.numops::Int`: 線形写像が適用された回数、すなわち `f` が呼び出された回数、またはベクトルが `A` と掛けられた回数です。
      * `info.numiter::Int`: Krylov 部分空間が再起動された回数（以下を参照）。

!!! warning "収束の確認"
    すべての要求された固有値が収束しなかった場合、警告は表示されないため、常に `info.converged >= howmany` を確認してください。


```
