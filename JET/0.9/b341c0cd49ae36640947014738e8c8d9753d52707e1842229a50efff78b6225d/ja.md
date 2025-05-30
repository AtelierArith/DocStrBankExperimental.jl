# JET.jl

[![](https://img.shields.io/badge/docs-latest-blue.svg)](https://aviatesk.github.io/JET.jl/dev/) [![](https://github.com/aviatesk/JET.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/aviatesk/JET.jl/actions/workflows/ci.yml) [![](https://codecov.io/gh/aviatesk/JET.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/aviatesk/JET.jl) [![](https://img.shields.io/badge/%F0%9F%9B%A9%EF%B8%8F_tested_with-JET.jl-233f9a)](https://github.com/aviatesk/JET.jl)

JETは、Juliaの型推論システムを利用して、潜在的なバグや型の不安定性を検出します。

```
[!NOTE]
現在の開発は[`release-0.10`](https://github.com/aviatesk/JET.jl/tree/release-0.10)ブランチに基づいています。
このブランチは、Julia v1.12のためにJET v0.10を安定させることに焦点を当てており、
[新しい言語サーバープロジェクト](https://github.com/aviatesk/JETLS.jl)との統合の準備をしています。
```

!!! warning
    JETはJuliaコンパイラと密接に統合されているため、JETが提示する結果は、使用しているJuliaのバージョンによって大きく異なる可能性があることに注意してください。さらに、Juliaにバンドルされている`Base`モジュールや標準ライブラリの実装も結果に影響を与える可能性があります。

    さらに、Juliaコンパイラのプラグインシステムはまだ不安定であり、そのインターフェースは頻繁に変更されるため、各バージョンのJETは限られたバージョンのJuliaとしか互換性がありません。Juliaパッケージマネージャーは、自動的にあなたのJuliaバージョンと互換性のある最新のJETバージョンを選択してインストールします。ただし、夜間ビルドのJuliaを使用している場合、互換性のあるJETバージョンがまだリリースされていない可能性があり、Juliaパッケージマネージャーを介してインストールされたJETが正しく機能しない場合があります。


## クイックスタート

[ドキュメント](https://aviatesk.github.io/JET.jl/dev/)で、さらに多くのコマンド、オプション、および説明を参照してください。

### インストール

JETは標準のJuliaパッケージです。したがって、Juliaの組み込みパッケージマネージャーを介してインストールし、他のパッケージと同様に使用できます。

```julia-repl noeval
julia> using Pkg; Pkg.add("JET")
[ some output elided ]

julia> using JET
```

### `@report_opt`で型の不安定性を検出

型の不安定性は、`@report_opt`マクロを使用して関数呼び出しで検出できます。このマクロは、`@code_warntype`マクロと似たように機能します。JETはJuliaの型推論に依存しているため、動的ディスパッチによって推論のチェーンが壊れると、すべての下流の関数呼び出しはコンパイラにとって不明となり、JETはそれらを分析できません。

```julia-repl
julia> @report_opt foldl(+, Any[]; init=0)
═════ 2 possible errors found ═════
┌ kwcall(::@NamedTuple{init::Int64}, ::typeof(foldl), op::typeof(+), itr::Vector{Any}) @ Base ./reduce.jl:198
│┌ foldl(op::typeof(+), itr::Vector{Any}; kw::@Kwargs{init::Int64}) @ Base ./reduce.jl:198
││┌ kwcall(::@NamedTuple{init::Int64}, ::typeof(mapfoldl), f::typeof(identity), op::typeof(+), itr::Vector{Any}) @ Base ./reduce.jl:175
│││┌ mapfoldl(f::typeof(identity), op::typeof(+), itr::Vector{Any}; init::Int64) @ Base ./reduce.jl:175
││││┌ mapfoldl_impl(f::typeof(identity), op::typeof(+), nt::Int64, itr::Vector{Any}) @ Base ./reduce.jl:44
│││││┌ foldl_impl(op::Base.BottomRF{typeof(+)}, nt::Int64, itr::Vector{Any}) @ Base ./reduce.jl:48
││││││┌ _foldl_impl(op::Base.BottomRF{typeof(+)}, init::Int64, itr::Vector{Any}) @ Base ./reduce.jl:58
│││││││┌ (::Base.BottomRF{typeof(+)})(acc::Int64, x::Any) @ Base ./reduce.jl:86
││││││││ runtime dispatch detected: +(acc::Int64, x::Any)::Any
│││││││└────────────────────
││││││┌ _foldl_impl(op::Base.BottomRF{typeof(+)}, init::Int64, itr::Vector{Any}) @ Base ./reduce.jl:62
│││││││┌ (::Base.BottomRF{typeof(+)})(acc::Any, x::Any) @ Base ./reduce.jl:86
││││││││ runtime dispatch detected: +(acc::Any, x::Any)::Any
│││││││└────────────────────
```

### `@report_call`で型エラーを検出

これは型が安定したコードで最も効果的に機能するため、`@report_call`を使用する前に`@report_opt`を自由に使用してください。

```julia-repl
julia> @report_call foldl(+, Char[])
═════ 2 possible errors found ═════
┌ foldl(op::typeof(+), itr::Vector{Char}) @ Base ./reduce.jl:198
│┌ foldl(op::typeof(+), itr::Vector{Char}; kw::@Kwargs{}) @ Base ./reduce.jl:198
││┌ mapfoldl(f::typeof(identity), op::typeof(+), itr::Vector{Char}) @ Base ./reduce.jl:175
│││┌ mapfoldl(f::typeof(identity), op::typeof(+), itr::Vector{Char}; init::Base._InitialValue) @ Base ./reduce.jl:175
││││┌ mapfoldl_impl(f::typeof(identity), op::typeof(+), nt::Base._InitialValue, itr::Vector{Char}) @ Base ./reduce.jl:44
│││││┌ foldl_impl(op::Base.BottomRF{typeof(+)}, nt::Base._InitialValue, itr::Vector{Char}) @ Base ./reduce.jl:48
││││││┌ _foldl_impl(op::Base.BottomRF{typeof(+)}, init::Base._InitialValue, itr::Vector{Char}) @ Base ./reduce.jl:62
│││││││┌ (::Base.BottomRF{typeof(+)})(acc::Char, x::Char) @ Base ./reduce.jl:86
││││││││ no matching method found `+(::Char, ::Char)`: (op::Base.BottomRF{typeof(+)}).rf::typeof(+)(acc::Char, x::Char)
│││││││└────────────────────
│││││┌ foldl_impl(op::Base.BottomRF{typeof(+)}, nt::Base._InitialValue, itr::Vector{Char}) @ Base ./reduce.jl:49
││││││┌ reduce_empty_iter(op::Base.BottomRF{typeof(+)}, itr::Vector{Char}) @ Base ./reduce.jl:383
│││││││┌ reduce_empty_iter(op::Base.BottomRF{typeof(+)}, itr::Vector{Char}, ::Base.HasEltype) @ Base ./reduce.jl:384
││││││││┌ reduce_empty(op::Base.BottomRF{typeof(+)}, ::Type{Char}) @ Base ./reduce.jl:360
│││││││││┌ reduce_empty(::typeof(+), ::Type{Char}) @ Base ./reduce.jl:343
││││││││││ no matching method found `zero(::Type{Char})`: zero(T::Type{Char})
│││││││││└────────────────────
```

### `report_package`でパッケージを分析

これはすべてのメソッド定義を探し、関数呼び出しをそのシグネチャに基づいて分析します。これは、実際の入力型が一般的なメソッドに対しては知られないため、`@report_call`よりも正確性が低いことに注意してください。

```julia-repl
julia> using Pkg; Pkg.activate(; temp=true, io=devnull); Pkg.add("AbstractTrees"; io=devnull);

julia> Pkg.status()
Status `/private/var/folders/xh/6zzly9vx71v05_y67nm_s9_c0000gn/T/jl_h07K2m/Project.toml`
  [1520ce14] AbstractTrees v0.4.4

julia> report_package("AbstractTrees")
[ some output elided ]
═════ 7 possible errors found ═════
┌ isroot(root::Any, x::Any) @ AbstractTrees ~/.julia/packages/AbstractTrees/EUx8s/src/base.jl:102
│ no matching method found `parent(::Any, ::Any)`: AbstractTrees.parent(root::Any, x::Any)
└────────────────────
┌ AbstractTrees.IndexNode(tree::Any) @ AbstractTrees ~/.julia/packages/AbstractTrees/EUx8s/src/indexing.jl:117
│ no matching method found `rootindex(::Any)`: rootindex(tree::Any)
└────────────────────
┌ parent(idx::AbstractTrees.IndexNode) @ AbstractTrees ~/.julia/packages/AbstractTrees/EUx8s/src/indexing.jl:127
│ no matching method found `parentindex(::Any, ::Any)`: pidx = parentindex((idx::AbstractTrees.IndexNode).tree::Any, (idx::AbstractTrees.IndexNode).index::Any)
└────────────────────
┌ nextsibling(idx::AbstractTrees.IndexNode) @ AbstractTrees ~/.julia/packages/AbstractTrees/EUx8s/src/indexing.jl:132
│ no matching method found `nextsiblingindex(::Any, ::Any)`: sidx = nextsiblingindex((idx::AbstractTrees.IndexNode).tree::Any, (idx::AbstractTrees.IndexNode).index::Any)
└────────────────────
┌ prevsibling(idx::AbstractTrees.IndexNode) @ AbstractTrees ~/.julia/packages/AbstractTrees/EUx8s/src/indexing.jl:137
│ no matching method found `prevsiblingindex(::Any, ::Any)`: sidx = prevsiblingindex((idx::AbstractTrees.IndexNode).tree::Any, (idx::AbstractTrees.IndexNode).index::Any)
└────────────────────
┌ prevsibling(csr::AbstractTrees.IndexedCursor) @ AbstractTrees ~/.julia/packages/AbstractTrees/EUx8s/src/cursors.jl:234
│ no matching method found `getindex(::Nothing, ::Int64)` (1/2 union split): (AbstractTrees.parent(csr::AbstractTrees.IndexedCursor)::Union{Nothing, AbstractTrees.IndexedCursor})[idx::Int64]
└────────────────────
┌ (::AbstractTrees.var"#17#18")(n::Any) @ AbstractTrees ~/.julia/packages/AbstractTrees/EUx8s/src/iteration.jl:323
│ no matching method found `parent(::Any, ::Any)`: AbstractTrees.parent(getfield(#self#::AbstractTrees.var"#17#18", :tree)::Any, n::Any)
└────────────────────
```

## 制限事項

JETは、あなたが直接呼び出す関数とその*推論可能な*呼び出し先を探索します。ただし、呼び出しの引数型が推論できない場合、JETは呼び出し先を分析しません。したがって、`No errors detected`という報告は、あなたのコードベース全体がエラーがないことを意味するわけではありません。JETの結果に対する信頼性を高めるために、`@report_opt`を使用してコードが推論可能であることを確認してください。

JETは[SnoopCompile](https://github.com/timholy/SnoopCompile.jl)と統合されており、時にはSnoopCompileを使用して、より包括的な分析を行うためのデータを収集できます。SnoopCompileの制限は、以前に推論されていない呼び出しのデータのみを収集するため、この種の分析を新しいセッションで実行する必要があることです。

詳細については、[SnoopCompileのJET統合ドキュメント](https://timholy.github.io/SnoopCompile.jl/stable/jet/)を参照してください。

## 謝辞

このプロジェクトは、京都大学での私の学部論文プロジェクトとして始まり、桜川隆教授の指導を受けました。私たちは、Rubyのための実験的な型理解/チェックツールである[ruby/typeprof](https://github.com/ruby/typeprof)から大きなインスピレーションを受けました。このプロジェクトに関する大学院論文は[https://github.com/aviatesk/grad-thesis](https://github.com/aviatesk/grad-thesis)に公開されていますが、現在は日本語のみで利用可能です。
