# Try.jl: ゼロオーバーヘッドでデバッグ可能なエラーハンドリング

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliapreludes.github.io/Try.jl/dev) [![CI](https://github.com/JuliaPreludes/Try.jl/actions/workflows/test.yml/badge.svg)](https://github.com/JuliaPreludes/Try.jl/actions/workflows/test.yml) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl)

特徴:

  * エラーハンドリングを*値*の単純な操作として扱う。
  * Julia言語とコンパイラのユニークな特性を活用して*推論可能性*と*最適化可能性*に焦点を当てる。
  * `throw`なしでエラーの発生源を特定するための*エラートレース*。
  * 特性ベースの機能検出に対する堅牢でミニマリスティックな代替手段として、["許可を求めるよりも許しを求める方が簡単" (EAFP)](https://docs.python.org/3/glossary.html#term-EAFP)アプローチを促進する。
  * 失敗可能な手続きを構成するための汎用的で拡張可能なツール。

詳細な説明については、下記の[ディスカッション](#discussion)を参照してください。

APIリファレンスについては[ドキュメント](https://juliapreludes.github.io/Try.jl/dev/)を参照してください。

## 例

### 基本的な使用法

デモンストレーションのために、Try.jlを使用してTry.jlを使用して構築された失敗可能なAPIの使い方を見てみましょう。

```jldoctest Try
julia> using Try

julia> using TryExperimental  # trygetindexなどをエクスポート
```

Try.jlベースのAPIは、`OK`値を返します。

```jldoctest Try
julia> ok = trygetindex(Dict(:a => 111), :a)
Try.Ok: 111
```

または`Err`値を返します：

```jldoctest Try
julia> err = trygetindex(Dict(:a => 111), :b)
Try.Err: KeyError: key :b not found
```

これらの値は一緒に*結果*値と呼ばれます。Try.jlは、述語関数などの結果値を扱うためのさまざまなツールを提供します。

```jldoctest Try
julia> Try.isok(ok)
true

julia> Try.iserr(err)
true
```

アンラップ関数：

```jldoctest Try
julia> Try.unwrap(ok)
111

julia> Try.unwrap_err(err)
KeyError(:b)
```

および[その他](https://juliapreludes.github.io/Try.jl/dev/)。

### エラートレース

エラーが深いスタックの関数呼び出しから「バブルアップ」する例を考えてみましょう：

```JULIA
julia> using Try, TryExperimental

julia> f1(x) = x ? Ok(nothing) : Err(KeyError(:b));

julia> f2(x) = f1(x);

julia> f3(x) = f2(x);
```

Try.jlはエラーを単純にJulia値として表現するため、デフォルトではこのエラーの発生源に関する情報はありません：

```JULIA
julia> f3(false)
Try.Err: KeyError: key :b not found
```

`Try.enable_errortrace()`を呼び出すことで、エラーのスタックトレース記録を有効にできます。

```JULIA
julia> Try.enable_errortrace();

julia> y = f3(false)
Try.Err: KeyError: key :b not found
Stacktrace:
 [1] f1
   @ ./REPL[2]:1 [inlined]
 [2] f2
   @ ./REPL[3]:1 [inlined]
 [3] f3(x::Bool)
   @ Main ./REPL[4]:1
 [4] top-level scope
   @ REPL[7]:1

julia> Try.disable_errortrace();
```

`f3`が例外をスローしなかったことに注意してください。`Err`型の値を返しました：

```JULIA
julia> Try.iserr(y)
true

julia> Try.unwrap_err(y)
KeyError(:b)
```

つまり、スタックトレースは単に「メタデータ」として添付され、`Try.enable_errortrace()`は`Err`値の動作を変更しません。

**制限/実装の詳細**: スタックトレースのキャプチャコストを排除するために、`Try.enable_errortrace()`はメソッドの無効化を使用して実装されています。したがって、すでに開始された`Task`に対してエラートレースを有効にすることはできません。

### EAFP

下記の[EAFPと特性](#eafp-and-traits)で説明されているように、`TryExperimental`で定義された`Base`-ライクなAPIは、メソッドが定義されていない場合にスローしません。たとえば、`trygeteltype`や`trygetlength`は、メソッドが定義されているかどうかを確認せずに任意のオブジェクトに対して呼び出すことができます（= "許しを求める"）。

```jldoctest Try
using Try, TryExperimental

function try_map_prealloc(f, xs)
    T = @? trygeteltype(xs)  # マクロベースのショートサーキット
    n = @? trygetlength(xs)
    ys = Vector{T}(undef, n)
    for (i, x) in zip(eachindex(ys), xs)
        ys[i] = f(x)
    end
    return Ok(ys)
end

mymap(f, xs) =
    try_map_prealloc(f, xs) |>
    Try.or_else() do _  # 関数合成
        Ok(mapfoldl(f, push!, xs; init = []))
    end |>
    Try.unwrap

mymap(x -> x + 1, 1:3)

# 出力
3-element Vector{Int64}:
 2
 3
 4
```

```jldoctest Try
mymap(x -> x + 1, (x for x in 1:5 if isodd(x)))

# 出力
3-element Vector{Any}:
 2
 4
 6
```

### 成功/失敗パスの排除

Try.jlを使用してエラーハンドリングを行う関数（例えば`Try.first`）は、通常、`Union{Ok,Err}`の戻り値の型を持ちます。したがって、コンパイラは時々、成功と失敗のパスの一部が決して取られないことを証明できます：

```jldoctest Try
julia> using TryExperimental, InteractiveUtils

julia> @code_typed(trygetfirst((111, "two", :three)))[2]  # 非空タプルの場合は常に成功
Ok{Int64}

julia> @code_typed(trygetfirst(()))[2]  # 空タプルの場合は常に失敗
Err{BoundsError}

julia> @code_typed(trygetfirst(Int[]))[2]  # 配列の場合は両方が可能
Union{Ok{Int64}, Err{BoundsError}}
```

### 戻り値のエラーを制約する

戻り値の型変換`function f(...)::ReturnType ...  end`を使用して、可能なエラー型を制約できます。これはJavaの`throws`キーワードに似ています。

これは、Try.jlベースの関数から期待されるエラーのセットのみが返されることを保証するために使用できます。特に、API境界で可能なエラーを制限するのに役立ちます。アイデアは、「呼び出しAPI」`f`を「オーバーロードAPI`__f__`から分離し、新しいメソッドが`__f__`に追加され、`f`には追加されないようにすることです。次に、戻り値の型を単に宣言する呼び出しAPI関数でオーバーロードAPI関数をラップできます：

```Julia
f(args...)::Result{Any,PossibleErrors} = __f__(args...)
```

次に、`f`のAPI仕様には、`__f__`のメソッド（`f`ではなく）を定義する必要があることを説明するオーバーロード指示を含めることができます。

以下は、オーバーロードAPI`__tryparse__`をラップする呼び出しAPI`tryparse`の例です。このおもちゃの例では、`__tryparse__`は`InvalidCharError()`または`EndOfBufferError()`をエラー値として返すことができます：

```jldoctest Try
using Try, TryExperimental

const Result{T,E} = Union{Ok{<:T},Err{<:E}}
# using TryExperimental: Result  # （ほぼ同等）

struct InvalidCharError <: Exception end
struct EndOfBufferError <: Exception end

const ParseError = Union{InvalidCharError, EndOfBufferError}

tryparse(T, str)::Result{T,ParseError} = __tryparse__(T, str)

function __tryparse__(::Type{Int}, str::AbstractString)
    isempty(str) && return Err(EndOfBufferError())
    Ok(@something(Base.tryparse(Int, str), return Err(InvalidCharError())))
end

tryparse(Int, "111")

# 出力
Try.Ok: 111
```

```jldoctest Try
tryparse(Int, "")

# 出力
Try.Err: EndOfBufferError()
```

```jldoctest Try
tryparse(Int, "one")

# 出力
Try.Err: InvalidCharError()
```

エラーを制約することは、エラーハンドリングが完全であることを保証するために、汎用プログラミングに役立ちます。このパターンは、*無効なエラーをプログラマーに直接報告する*ことを容易にします（[いつ`throw`するか？いつ`return`するか？](#when-to-throw-when-to-return)を参照）が、正しく実装されたメソッドは実行時のオーバーヘッドを発生させません。

また、[julep: "chain of custody" error handling · Issue #7026 · JuliaLang/julia](https://github.com/JuliaLang/julia/issues/7026)も参照してください。

## ディスカッション

Juliaは動的言語であり、コンパイラは動的性を積極的に最適化して静的言語に匹敵するパフォーマンスを得ることができます。そのため、Juliaの多くの成功した機能は、動的言語の使いやすさを提供しながら、構成されたコードの最適化可能性に注意を払っています。しかし、ネイティブの`throw`/`catch`ベースの例外は積極的に最適化されず、既存の「静的」ソリューションは、プログラミングの高レベルスタイルをサポートしていません。Try.jlは、Juliaの動的性を受け入れつつ、コンパイラが最適化できる形にできるだけ制限する[代替ソリューション](https://xkcd.com/927/)を探求しています。

### *アクション*に焦点を当てる; タイプではなく

Try.jlは、失敗可能な手続きを構成するための汎用ツールを提供することを目指しています。この*アクション*を実行することに重点を置くことは、タイプに焦点を当てた他の[類似のJuliaパッケージ](#similar-packages)と対照的であり、パッケージの名前にも反映されています：*Try*。これは、Juliaのような動的プログラミング言語のAPI設計における重要なガイドラインであり、高レベルのコードはタイプを管理することなく表現可能であるべきです。

たとえば、Try.jlは、`Union{Ok,Err}`だけでなく、ショートサーキット評価のための[API](https://juliapreludes.github.io/Try.jl/dev/#Short-circuit-evaluation)を提供しています：

```jldoctest Try
julia> Try.and_then(Ok(1)) do x
           Ok(x + 1)
       end
Try.Ok: 2

julia> Try.and_then(Ok(1)) do x
           iszero(x) ? Ok(x) : Err("not zero")
       end
Try.Err: "not zero"
```

また、`Union{Some,Nothing}`に対しても：

```jldoctest Try
julia> Try.and_then(Some(1)) do x
           Some(x + 1)
       end
Some(2)

julia> Try.and_then(Some(1)) do x
           iszero(x) ? Some(x) : nothing
       end
```

上記のコードスニペットでは、成功と失敗に関する情報を伝えるために、`Ok`、`Err`、`Some`のコンストラクタが必要です。

もちろん、Juliaでは、タイプを使用して効率的かつ柔軟に実行を制御できます。実際、さまざまなショートサーキット評価に必要なメカニズムは、[ショートサーキット評価インターフェース](https://juliapreludes.github.io/Try.jl/dev/experimental/#customize-short-circuit)（実験的）を定義することによって、任意のユーザー定義タイプに使用できます。

### 最適化可能性を最大化するための動的な戻り値の型

Try.jlは、Rustの`Result`型と`Try`トレイトに触発されたAPIを提供します。しかし、Juliaの力を完全に引き出すために、Try.jlは具体的に型付けされた`struct`型の代わりに*小さな`Union`型*を使用します。これは、出力型を手動で計算することを避ける、イディオマティックでクリーンな高レベルのJuliaコードにとって不可欠です。しかし、この分野での以前のすべての試み（[ErrorTypes.jl](https://github.com/jakobnissen/ErrorTypes.jl)、[ResultTypes.jl](https://github.com/iamed2/ResultTypes.jl)、および[Expect.jl](https://github.com/KristofferC/Expect.jl)など）は、結果値を表すために`struct`型を使用しています（[`ErrorTypes.Result`](https://github.com/jakobnissen/ErrorTypes.jl/blob/c3a7d529716ebfa3ee956049f77f606b6c00700b/src/ErrorTypes.jl#L45-L47)、[`ResultTypes.Result`](https://github.com/iamed2/ResultTypes.jl/blob/42ebadf4d859964efa36ebccbeed3d5b65f3e9d9/src/ResultTypes.jl#L5-L8)、および[`Expect.Expected`](https://github.com/KristofferC/Expect.jl/blob/6834049306c2b53c1666cbed504655e36b56e3b4/src/Expect.jl#L6-L9)を参照）。具体的に型付けされた`struct`を戻り値の型として使用することには、型推論の結果を制御しやすいという利点があります。しかし、これはユーザーに未取得のパスの型を手動で計算させることを強いることになります。これは面倒であり、時には単に不可能です。これは、出力型の計算をコンパイラに委任するのが一般的なJuliaコードではありません。さらに、型安定化の利点は、成功および/または失敗の分岐を排除する機会を失う代償を伴います（上記の[成功/失敗パスの排除](#successfailure-path-elimination)を参照）。具体的な`struct`アプローチでも、（推論後の）インライン化、集約のスカラー置換、およびデッドコード排除の組み合わせにより、同様の最適化が原則として発生する可能性があります。しかし、型推論はJuliaコンパイラにおける手続き間分析と最適化の主な原動力であるため、`Union`戻り値の型は、コンパイラにコードの意図を伝える最も効果的な方法であり続ける可能性が高いです（たとえば、関数呼び出しが常に成功する場合、常に`Ok{T}`を返す）。

（とはいえ、Try.jlは、`Union`が適切でない場合に具体的に型付けされた戻り値のサポートも含んでいます。これは、そのような手動の「型不安定性隠蔽」が大規模で実行可能なアプローチであるかどうか、また、魅力的な均一APIを提供できるかどうかを実験するためです。）

### デバッグ可能なエラーハンドリング

`Result`型を使用する際の潜在的な使いやすさの問題は、ユーザーがエラーを受け取った時点でエラーの詳細なコンテキストが失われることです。これにより、単に例外を`throw`するのに比べてJuliaプログラムのデバッグが難しくなります。この問題を軽減するために、Try.jlはエラーのバックトレースを記録するための*エラートレース*メカニズムを提供します。これは、実行時に`Try.enable_errortrace()`を使用して切り替えることができます。これは、Zigの[エラー戻りトレース](https://ziglang.org/documentation/master/#Error-Return-Traces)に触発されています。

### EAFPと特性

TryExperiments.jlは、Try.jl APIのデモンストレーションとして、`trytake!`などのJulia `Base`に基づく限られたセットの「動詞」を実装しています。これらの関数には、`Err{<:NotImplementedError}`型のエラー値を返すキャッチオールのデフォルト定義があります。これにより、実行時の`MethodError`例外を取得することなく呼び出すことができるため、["許可を求めるよりも許しを求める方が簡単" (EAFP)](https://docs.python.org/3/glossary.html#term-EAFP)の方法でこれらの関数を使用できます。重要なことに、EAFPアプローチは、実装者が宣言された特性（例：`HasLength`）が実際の定義（例：`length`）と互換性があることを確認しなければならない特性ベースの機能検出の問題を持っていません。EAFPアプローチでは、*機能はそれを提供するメソッドの定義によって自動的に宣言されます*（例：`trygetlength`）。したがって、構造上、機能の宣言と定義が同期しないようにすることは困難です。もちろん、このアプローチは、ナイーブに適用された場合、効果のないまたは「再実行可能な」関数にのみ機能します。破壊的操作のシーケンスが可能かどうかを確認するには、特性ベースのアプローチが非常に簡単です。効果的な計算のためにEAFPアプローチを使用する1つの方法は、最初のフェーズでEAFP方式で効果を適用する方法のレシピを構築し、2番目のフェーズで効果を適用する低レベルの二相APIを作成することです。

（使用上の注意：EAFP互換の関数は、`function f end`の代わりに`@tryable f`で宣言できます。これにより、自動的に`Err{<:NotImplementedError}`を返すキャッチオールフォールバックメソッドが定義されます。）

#### `hasmethod`と`applicable`（および`invoke`）に関する補足

Try.jlを使用したEAFPアプローチは、`hasmethod`および/または`applicable`を使用した["飛び込む前に見て" (LBYL)](https://docs.python.org/3/glossary.html#term-LBYL)の対応物と同等ではないことに注意してください。`f(x)`を呼び出す前に`applicable(f, x)`をチェックすることは、手動コーディングなしで行えるため魅力的に見えるかもしれません。しかし、このLBYLアプローチは、汎用機能検出には根本的に使えません。これは、`hasmethod`と`applicable`が次のような「内部ディスパッチ」を持つ「ブランケット定義」を処理できないためです：

```jldoctest Try
julia> f(x::Real) = f_impl(x);  # ブランケット定義

julia> f_impl(x::Int) = x + 1;  # 内部ディスパッチ

julia> applicable(f, 0.1)
true

julia> hasmethod(f, Tuple{Float64})
true
```

`f(0.1)`が`MethodError`をスローするにもかかわらず、`applicable`や`hasmethod`を信頼する場合、`f(0.1)`が呼び出し可能であると見なされます。したがって、`applicable`と`hasmethod`の結果は、`f`のオーバーロード指示が上記のようなブランケット定義を特に禁止しない限り、信頼できません。（まったく同じ理由で、ライブラリ関数に対する`invoke`の使用も問題があります。）

EAFPアプローチは、実際のコードパスが「動的に機能を宣言」するために機能します。

### いつ`throw`するか？いつ`return`するか？

2つのエラーレポートモード（すなわち、例外を`throw`することと`Err`値を`return`すること）を持つことは、正当化されるべき複雑さを導入します。Try.jlは、コンパイラが`try`-`catch`を最適化できるまでの回避策に過ぎないのでしょうか？（「はい」は合理的な答えかもしれません。）それとも、これらの使用ケースを区別する原則的な方法があるのでしょうか？（これがここで探求されていることです。）

`return`によるエラー報告は、特にエラーハンドリングがタイトなループで行われる場合に便利です。たとえば、同時データ構造APIを構成する際には、タイトなループ内で失敗モード（例：論理的失敗と一時的/競合失敗）を知る必要があることがあります。Juliaコンパイラは、Try.jlのエラーハンドリングを単純なフラグベースの低レベルコードに最適化できる可能性があります。このスタイルのプログラミングには、特定のエラーが報告される条件に関するAPIの明確な定義が必要です。つまり、そのようなAPIは、特定の満たされていない「前提条件」の検出を保証し、呼び出しプログラムがこれらのエラーから回復する方法を持つことが期待されます。

対照的に、呼び出しプログラムがエラーから回復する方法がなく、エラーが*人間*に報告されるべき場合、例外を`throw`する方が適切です。たとえば、データ構造の内部状態の不整合が検出された場合、それは使用または実装のバグである可能性が高いです。この場合、呼び出しプログラムはそのような契約違反エラーから回復する方法がなく、唯一の人間のプログラマーが行動を取ることができます。Juliaの典型的なインタラクティブなワークフローをサポートするために、エラーを印刷してプログラム全体を中止することは選択肢ではありません。したがって、Juliaでは契約違反エラーからも回復できることが重要です。このような言語構造は、REPLやエディタプラグインなどのプログラミングツールを構築するために必要です。要約すると、`return`ベースのエラーレポートは回復可能なエラーに適しており、`throw`ベースのエラーレポートは回復不可能（すなわちプログラマーの）エラーに適しています。

### リンク

#### 類似のパッケージ

  * [ErrorTypes.jl](https://github.com/jakobnissen/ErrorTypes.jl)
  * [ResultTypes.jl](https://github.com/iamed2/ResultTypes.jl)
  * [Expect.jl](https://github.com/KristofferC/Expect.jl)

#### その他のディスカッション

  * [迅速なエラーハンドリングのための結果値の慣習を持つことはできますか？ · ディスカッション #43773 · JuliaLang/julia](https://github.com/JuliaLang/julia/discussions/43773)
  * [Try.jl - JuliaLang - Zulip](https://julialang.zulipchat.com/#narrow/stream/137791-general/topic/Try.2Ejl)
  * [[ANN] ErrorTypes.jl - Rustのような安全なエラーをJuliaで - パッケージアナウンス/パッケージアナウンス - JuliaLang](https://discourse.julialang.org/t/ann-errortypes-jl-rust-like-safe-errors-in-julia/53953)
