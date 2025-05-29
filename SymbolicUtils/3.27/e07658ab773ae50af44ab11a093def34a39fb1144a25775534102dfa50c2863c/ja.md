# SymbolicUtils.jl

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/SymbolicUtils/stable/)

[![codecov](https://codecov.io/gh/JuliaSymbolics/SymbolicUtils.jl/branch/master/graph/badge.svg)](https://app.codecov.io/gh/JuliaSymbolics/SymbolicUtils.jl) [![Build Status](https://github.com/JuliaSymbolics/SymbolicUtils.jl/workflows/CI/badge.svg)](https://github.com/JuliaSymbolics/SymbolicUtils.jl/actions?query=workflow%3ACI) [![Build status](https://badge.buildkite.com/3db222e469784b365e4b45f2b0155d252cf0ae70fef708bfa1.svg?branch=master)](https://buildkite.com/julialang/symbolicutils-dot-jl)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

## チュートリアルとドキュメント

パッケージの使用に関する情報は、[安定版のドキュメント](https://docs.sciml.ai/SymbolicUtils/stable/)を参照してください。未公開の機能を含むドキュメントのバージョンについては、[開発中のドキュメント](https://docs.sciml.ai/SymbolicUtils/dev/)を使用してください。

SymbolicUtils.jlは、シンボリック計算のためのさまざまなユーティリティを提供します。SymbolicUtils.jlは、コンピュータ代数システム（CAS）を構築するために使用されるものです。SymPyやMathematicaに似た完全なCASを探している場合は、[Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)を参照してください。奇妙なオクタニオン代数のためのクレイジーなCASを構築したい場合は、正しい場所に来ています。

[SymbolicUtilsのシンボル](https://docs.sciml.ai/SymbolicUtils/stable/#Creating-symbolic-expressions)は型情報を持っています。それらに対する操作はこの情報を伝播させます。[ルールベースの書き換え言語](https://docs.sciml.ai/SymbolicUtils/stable/manual/rewrite/)を使用して、任意の条件を満たす部分式を見つけ、マッチに対して任意の変換を適用できます。このライブラリには、数値シンボルと数の式に対する便利な[簡約](https://docs.sciml.ai/SymbolicUtils/stable/#Simplification)ルールのセットも含まれています。これらは特別な目的のためにリミックスおよび拡張できます。

独自の型のためのルール書き換えシステムが必要なJuliaパッケージ開発者は、[インターフェースガイド](https://docs.sciml.ai/SymbolicUtils/stable/manual/interface/#Interfacing-with-SymbolicUtils.jl)を確認してください。

### "マニュアルを読みたくない、クールなコードを見せて"

```julia
julia> using SymbolicUtils

julia> SymbolicUtils.show_simplified[] = true

julia> @syms x::Real y::Real z::Complex f(::Number)::Real
(x, y, z, f(::Number)::Real)

julia> 2x^2 - y + x^2
(3 * (x ^ 2)) + (-1 * y)

julia> f(sin(x)^2 + cos(x)^2) + z
f(1) + z

julia> r = @rule sinh(im * ~x) => sin(~x)
sinh(im * ~x) => sin(~x)

julia> r(sinh(im * y))
sin(y)

julia> simplify(cos(y)^2 + sinh(im*y)^2, RuleSet([r]))
1
```

# 引用

  * パターンマッチャーは、Gerald Jay Sussmanによるものの適応です（MITの[6.945](https://groups.csail.mit.edu/mac/users/gjs/6.945/)で見られるように）、彼の書籍[SICM](https://groups.csail.mit.edu/mac/users/gjs/6946/sicm-html/book.html)におけるシンボリックプログラミングの使用がこのパッケージにインスピレーションを与えました。
  * [Rewrite.jl](https://github.com/HarrisonGrodin/Rewrite.jl)および[Simplify.jl](https://github.com/HarrisonGrodin/Simplify.jl)は、[Harrison Grodin](https://github.com/HarrisonGrodin)によってもこのパッケージにインスピレーションを与えました。
