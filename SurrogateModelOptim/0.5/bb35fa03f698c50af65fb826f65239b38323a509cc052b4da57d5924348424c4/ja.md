<img src="docs/src/assets/logo.png" width="180">

# SurrogateModelOptim

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://MrUrq.github.io/SurrogateModelOptim.jl/stable) [![Build Status](https://travis-ci.org/MrUrq/SurrogateModelOptim.jl.svg?branch=master)](https://travis-ci.org/MrUrq/SurrogateModelOptim.jl) [![Codecov](https://codecov.io/gh/MrUrq/SurrogateModelOptim.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/MrUrq/SurrogateModelOptim.jl) [![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active) <!– [![Build Status](https://ci.appveyor.com/api/projects/status/github/MrUrq/SurrogateModelOptim.jl?svg=true)](https://ci.appveyor.com/project/MrUrq/SurrogateModelOptim-jl) –>

<!– [![Coveralls](https://coveralls.io/repos/github/MrUrq/SurrogateModelOptim.jl/badge.svg?branch=master)](https://coveralls.io/github/MrUrq/SurrogateModelOptim.jl?branch=master) –>

*SurrogateModelOptim* は高コストな関数の最適化のためのJuliaパッケージです。サロゲートモデルは、適応的な軸スケーリングを持つラジアル基底関数補間器のアンサンブルに基づいています。詳細については、私たちの[論文](https://doi.org/10.1016/j.asoc.2019.106050)を参照してください。

## インストール

このパッケージは登録されており、`Pkg.add`でインストールできます。

```julia
julia> Pkg.add("SurrogateModelOptim")
```

## 最適化

このパッケージは高コストな関数に使用することを意図しています。ここでの高コストとは、評価に数分から数日かかる関数を指します。最も簡単な使用法は次のとおりです。

```julia
julia> using SurrogateModelOptim
julia> rosenbrock_2D(x) = (1.0 - x[1])^2 + 100.0 * (x[2] - x[1]^2)^2
julia> search_range=[(-5.0,5.0),(-5.0,5.0)]
julia> smoptimize(rosenbrock_2D, search_range)
```

オプションインターフェースを通じてアクセス可能な多くのオプションがあります。デフォルトのオプションは、パフォーマンスの理由からマイナーバージョン間で更新される可能性があることに注意してください。目標は関数値を最小化することです。モデルはラテンハイパーキューブサンプリングプランから作成されます。いくつかのラジアル基底関数サロゲートモデルがデータにフィットされ、サロゲートのアンサンブルが新しい設計位置を予測するために使用されます。新しい設計が追加され、サロゲートモデルを活用しつつ設計空間を探索します。

複数のサロゲートを作成するコストが高いため、サロゲートモデルを並行して作成することを強くお勧めします。`> julia -p x`でjuliaを並行して開始します。ここで`x`は利用可能なコアの数です。前の例は次のように実行できます。

```julia
julia> result = smoptimize(rosenbrock_2D, search_range;
                    options=SurrogateModelOptim.Options(
                    iterations=25,
                    num_interpolants=N*x, #Nは整数
                    num_start_samples=5,
                        ));
```

`num_interpolants=10`は、サロゲートモデルのアンサンブルが10のRBF補間器を含むことを意味し、さまざまな関数に対して良好なパフォーマンスを示しています。

## ドキュメント

  * [**STABLE**][docs-stable-url] &mdash; **ドキュメントのタグ付けされたバージョン。**

## 著者

  * Magnus Urquhart - [@MrUrq](https://github.com/MrUrq/)

[docs-stable-img]: https://img.shields.io/badge/docs-stable-blue.svg [docs-stable-url]: https://MrUrq.github.io/SurrogateModelOptim.jl/stable

### 引用

```
@article{urquhart_surrogate-based_2020,
	title = {適応的にスケーリングされたラジアル基底関数を用いたサロゲートベースの最適化},
	volume = {88},
	issn = {1568-4946},
	doi = {10.1016/j.asoc.2019.106050},
	journal = {Applied Soft Computing},
	author = {Urquhart, Magnus and Ljungskog, Emil and Sebben, Simone},
	year = {2020},
}
```
