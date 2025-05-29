<div align="center"> <picture>   <source media="(prefers-color-scheme: dark)" srcset="docs/src/assets/logo-dark.svg">   <source media="(prefers-color-scheme: light)" srcset="docs/src/assets/logo.svg">   <img alt="Infiltrator Logo" src="docs/src/assets/logo.svg" width="150px"> </picture> </div>

# Infiltrator.jl

[![CI](https://github.com/JuliaDebug/Infiltrator.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/JuliaDebug/Infiltrator.jl/actions/workflows/CI.yml) [![Codecov](https://codecov.io/gh/JuliaDebug/Infiltrator.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/JuliaDebug/Infiltrator.jl) [![version](https://juliahub.com/docs/Infiltrator/version.svg)](https://juliahub.com/ui/Packages/Infiltrator/ge3PS)

[![docs stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadebug.github.io/Infiltrator.jl/stable) [![docs dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliadebug.github.io/Infiltrator.jl/dev)

このパッケージは、実行時のパフォーマンスオーバーヘッドがほとんどないブレークポイントとして機能する`@infiltrate`マクロを提供します。

他の関数スコープにアクセスしたり、さらに呼び出しにステップインしたりすることはできません。そのレベルの柔軟性が必要な場合は、実際のデバッガを使用してください。

VS CodeやJunoでインライン評価を介して`@infiltrate` REPLモードをトリガーするコードを実行すると問題が発生する可能性があるため、常にREPLを直接使用することをお勧めします。

## `@infiltrate`

```julia
@infiltrate
@infiltrate condition::Bool
```

`@infiltrate`は浸透ポイントを設定します。

浸透ポイントに到達すると、ローカル変数やコールスタックを検査し、現在のローカルおよびグローバルスコープのコンテキストで任意のステートメントを実行できるインタラクティブなREPLセッションに入ります。

オプションの引数`cond`は、`true`に評価される場合にのみこの浸透ポイントを有効にします。例えば：

```julia
@infiltrate false # 浸透しない
```

次のように使用することもできます。

```julia
if isdefined(Main, :Infiltrator)
  Main.infiltrate(@__MODULE__, Base.@locals, @__FILE__, @__LINE__)
end
```

モジュールに対する事後評価なしでパッケージコードに浸透するために使用できます（関数形はコンパイル時にInfiltratorをロードする必要がないため）。

## セーフハウス

変数のエクスフィルタ（`@exfiltrate`または`@infiltrate`セッション内での代入による）は、変数をグローバルストレージスペース（モジュールによってバックアップされる）に割り当てることによって行われます。エクスフィルタされたオブジェクトは、`Infiltrator.store`またはそのエクスポートされたエイリアス`safehouse`または`exfiltrated`を介して直接アクセスできます：

```julia
julia> foo(x) = @exfiltrate
foo (generic function with 1 method)

julia> foo(3)

julia> safehouse.x # または exfiltrated.x
3
```

`Infiltrator.clear_store!()`を使用してセーフハウスをリセットできます。

特定のモジュールを`Infiltrator.set_store!(mod)`で割り当てることもできます。これにより、例えばバックモジュールを`Main`に設定し、セーフハウスの内容をグローバル名前空間にエクスポートすることができます（ただし、これを行うことは推奨されません）。

## 使用法

### スクリプトとパッケージ開発

Infiltratorをパッケージやスクリプトのデバッグに使用するには、少し設定が必要です。

1. 現在の環境または[環境スタック](https://docs.julialang.org/en/v1/manual/code-loading/#Environment-stacks)のさらに下にある環境にはInfiltrator.jlが含まれている必要があります。Infiltrator.jlをグローバル`@v1.xx`環境に入れておくことをお勧めします。そうすれば常に利用可能です。
2. [Revise.jl](https://github.com/timholy/Revise.jl)をロードするか、[VS Codeのインライン評価](https://www.julia-vscode.org/docs/stable/userguide/runningcode/)を使用して、パッケージコードをシームレスに更新します。
3. パッケージをロードします。
4. 必要な場所に`Main.@infiltrate`ステートメントをブレークポイントとして追加します。
5. ブレークポイントを含むメソッドを実行する関数を実行します。

ステップ3と4の順序は重要です。`Main.@infiltrate`ステートメントを追加した後にパッケージをロードすると、プリコンパイル中にそのマクロが存在しないため、ロードが妨げられます。

初期にコードをロードした後に絶対に変更できない場合は、`infiltrate`関数を代わりに使用することができます。マクロ形式の利点は、テストに失敗するため、浸透ポイントを含むコードをコミットまたはマージすることがないことです。

### REPLセッション

```julia
julia> function f(x)
         out = []
         for i in x
           push!(out, 2i)
           @infiltrate
         end
         out
       end
f (generic function with 1 method)

julia> f([1,2,3,4,5,6,7,8,9,10])
Infiltrating f(x::Vector{Int64})
  at REPL[10]:5

infil> ?
  ここに入力されたコードは現在のスコープで評価されます。ローカル変数の変更はできません。グローバル変数はeval/@evalでのみ変更できます。

  すべての代入はセーフハウスに入ります。

  次のコマンドは特別に処理されます：

    •  ?: このヘルプテキストを印刷します。

    •  @trace: 現在のスタックトレースを印刷します。

    •  @locals: ローカル変数を印刷します。@locals x yはxとyのみを印刷します。

    •  @exception: 現在の@infiltryセッションをトリガーした例外を印刷します（あれば）。

    •  @exfiltrate: すべてのローカル変数をストアに保存します。@exfiltrate x yはxとyを保存します。このバリアントは、infil> REPLで定義された変数もエクスフィルタできます。

    •  @toggle: この@infiltrateスポットでの浸透をトグルします（すべてをクリアするにはInfiltrator.clear_disabled!()を使用します）。

    •  @cond expr: <expr>がtrueに評価される場合にのみこの@infiltrateスポットで浸透します（すべてをクリアするにはInfiltrator.clear_conditions!()を使用します）。

    •  @continue: 次の浸透ポイントに進むか、終了します（ショートカット: Ctrl-D）。

    •  @doc symbol: シンボルのヘルプを取得します（通常のJulia REPLと同じです）。

    •  @exit: このセッションの残りの間、浸透を停止し、終了します。

infil> @locals
- out::Vector{Any} = Any[2]
- i::Int64 = 1
- x::Vector{Int64} = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

infil> 0//0
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
 [1] __throw_rational_argerror_zero(T::Type)
   @ Base ./rational.jl:32
 [2] Rational{Int64}(num::Int64, den::Int64)
   @ Base ./rational.jl:34
 [3] Rational
   @ ./rational.jl:39 [inlined]
 [4] //(n::Int64, d::Int64)
   @ Base ./rational.jl:62
 [5] top-level scope
   @ none:1

infil> @toggle
この浸透ポイントでの浸透を無効にしました。

infil> @toggle
この浸透ポイントでの浸透を有効にしました。

infil> @cond i > 5
この浸透ポイントでの浸透を条件付きで有効にしました。

infil> @continue

Infiltrating f(x::Vector{Int64})
  at REPL[10]:5

infil> i
6

infil> intermediate = copy(out)
6-element Vector{Any}:
  2
  4
  6
  8
 10
 12

infil> @exfiltrate intermediate x
2つのローカル変数をセーフハウスにエクスフィルタしています。

infil> @exit

10-element Vector{Any}:
  2
  4
  6
  8
 10
 12
 14
 16
 18
 20


julia> safehouse.intermediate
6-element Vector{Any}:
  2
  4
  6
  8
 10
 12

julia> @withstore begin
         x = 23
         x .* intermediate
       end
6-element Vector{Int64}:
  46
  92
 138
 184
 230
 276
```

## 高度な内容

### Infiltrator.jlの自動ロード

Infiltratorは非常に速くロードされます（私のマシンでは約3ms）し、`startup.jl`にロードするのは一般的に安全です。

何らかの理由で`startup.jl`にInfiltratorを無条件にロードしたくない場合は、代わりに次の便利なマクロを使用できます。これにより、Infiltrator.jlが自動的にロードされ（環境スタックにある場合）、その後`@infiltrate`が呼び出されます：

```julia
macro autoinfiltrate(cond=true)
    pkgid = Base.PkgId(Base.UUID("5903a43b-9cc3-4c30-8d17-598619ec4e9b"), "Infiltrator")
    if !haskey(Base.loaded_modules, pkgid)
        try
            Base.eval(Main, :(using Infiltrator))
        catch err
            @error "Infiltrator.jlをロードできません。環境スタックに含まれていることを確認してください。"
        end
    end
    i = get(Base.loaded_modules, pkgid, nothing)
    lnn = LineNumberNode(__source__.line, __source__.file)

    if i === nothing
        return Expr(
            :macrocall,
            Symbol("@warn"),
            lnn,
            "Infiltratorをロードできませんでした。")
    end

    return Expr(
        :macrocall,
        Expr(:., i, QuoteNode(Symbol("@infiltrate"))),
        lnn,
        esc(cond)
    )
end
```

## 関連プロジェクト

  * [`@exfiltrate` for Python](https://github.com/NightMachinary/PyExfiltrator)
