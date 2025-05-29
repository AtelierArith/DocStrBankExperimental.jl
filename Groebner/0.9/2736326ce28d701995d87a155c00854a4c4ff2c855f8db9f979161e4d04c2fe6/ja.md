<div align="left">     <picture>         <source media="(prefers-color-scheme: dark)" srcset="https://github.com/sumiya11/Groebner.jl/raw/master/docs/assets/logo-dark-with-text.svg">       <img alt="Groebner.jl logo" src="https://github.com/sumiya11/Groebner.jl/raw/master/docs/assets/logo-with-text.svg">     </picture> </div>

---

[![Runtests](https://github.com/sumiya11/Groebner.jl/actions/workflows/Runtests.yml/badge.svg)](https://github.com/sumiya11/Groebner.jl/actions/workflows/Runtests.yml) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://sumiya11.github.io/Groebner.jl) [![codecov](https://codecov.io/github/sumiya11/Groebner.jl/graph/badge.svg?token=J1SZT8ED9S)](https://codecov.io/github/sumiya11/Groebner.jl)

Groebner.jlは、体上のグレブナー基底を計算するためのJuliaパッケージです。Groebner.jlはGNU GPL v2の下で配布されています。

ドキュメントについては、https://sumiya11.github.io/Groebner.jlをご覧ください。簡単な例については、以下を参照してください。

開発計画については、[Plans for 2025](https://github.com/sumiya11/Groebner.jl/issues/177)をご覧ください。

## インストール

Juliaパッケージマネージャを使用してGroebner.jlをインストールできます。Julia REPLから、次のように入力します。

```julia
import Pkg; Pkg.add("Groebner")
```

インストール後、次のコマンドでパッケージのテストを実行できます。

```julia
import Pkg; Pkg.test("Groebner")
```

## Groebner.jlの使い方

Groebner.jlが提供する主な関数は`groebner`です。これは、AbstractAlgebra.jl、DynamicPolynomials.jl、およびNemo.jlの多項式と連携して動作します。

### AbstractAlgebra.jlを使用する場合

3つの変数の多項式環と単純な多項式系を作成します。

```julia
using AbstractAlgebra

R, (x1, x2, x3) = QQ["x1", "x2", "x3"]

system = [
  x1 + x2 + x3,
  x1*x2 + x1*x3 + x2*x3,
  x1*x2*x3 - 1
]
```

そして、`groebner`にシステムを渡してグレブナー基底を計算します。

```julia
using Groebner

G = groebner(system)
```

```julia
# 結果
3-element Vector{AbstractAlgebra.Generic.MPoly{Rational{BigInt}}}:
 x3^3 - 1
 x2^2 + x2*x3 + x3^2
 x1 + x2 + x3
```

### DynamicPolynomials.jlを使用する場合

AbstractAlgebra.jlと同様に、多項式のシステムを作成し、`groebner`に渡します。

```julia
using DynamicPolynomials, Groebner

@polyvar x1 x2
system = [10*x1*x2^2 - 11*x1 + 10,
        10*x1^2*x2 - 11*x2 + 10]

G = groebner(system)
```

```julia
# 結果
3-element Vector{Polynomial{DynamicPolynomials.Commutative{DynamicPolynomials.CreationOrder}, Graded{LexOrder}, Rational{BigInt}}}:
 10//11x2 - 10//11x1 - x2² + x1²
 1//1 - 11//10x2 - 10//11x2² + 10//11x1x2 + x2³
 1//1 - 11//10x1 + x1x2²
```

## 連絡先

このライブラリはアレクサンダー・デミン（<asdemin_2@edu.hse.ru>）によって維持されています。

## 貢献

貢献は大歓迎です。機能リクエストや提案も歓迎します。特に追加の例やドキュメントの改善が奨励されます。問題が発生した場合は、イシューを開くか、メンテナに連絡してください。

## 謝辞

私たちは、msolveライブラリの開発者に感謝します（[https://msolve.lip6.fr/](https://msolve.lip6.fr/)）。Groebner.jlのいくつかのコンポーネントはmsolveから適応されました。私たちのF4実装では、モノミアルハッシュテーブル、クリティカルペア処理、シンボリック前処理、線形代数のコードをmsolveから適応し調整しています。msolveのソースコードは[https://github.com/algebraic-solving/msolve](https://github.com/algebraic-solving/msolve)で入手できます。

ウラジミール・クズネツォフに有益な議論と彼のF4実装のソースを提供してくれたことに感謝します。

計算リソースを提供してくれたマックス・プランク情報学研究所、l'XのMAXチーム、InriaのOURAGANチームに感謝します。

## その他

グレブナー基底の計算に使用できるJuliaの他のソフトウェア：

  * [AlgebraicSolving.jl](https://github.com/algebraic-solving/AlgebraicSolving.jl)
  * [GroebnerBasis.jl](https://github.com/ederc/GroebnerBasis.jl)、非推奨、[Oscar.jl](https://github.com/oscar-system/Oscar.jl)を参照
  * [Singular.jl](https://github.com/oscar-system/Singular.jl)

ここにあなたのパッケージが見当たらない場合、私たちはそれを知らないか、含めるのを忘れた可能性があります。申し訳ありません！PRをオープンしてください。

## Groebner.jlの引用

Groebner.jlがあなたの作業に役立つと感じた場合、このリポジトリにスターを付け、[この論文](https://arxiv.org/abs/2304.06935)を引用してください。

```
@misc{demin2024groebnerjl,
      title={Groebner.jl: A package for Gr\"obner bases computations in Julia}, 
      author={Alexander Demin and Shashi Gowda},
      year={2024},
      eprint={2304.06935},
      archivePrefix={arXiv},
      primaryClass={cs.MS}
}
```
