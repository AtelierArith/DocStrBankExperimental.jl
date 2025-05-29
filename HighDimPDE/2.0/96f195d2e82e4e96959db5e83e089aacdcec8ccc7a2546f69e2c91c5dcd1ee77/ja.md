[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/HighDimPDE/stable/)

[![codecov](https://codecov.io/gh/SciML/HighDimPDE.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/SciML/HighDimPDE.jl) [![Build Status](https://github.com/SciML/HighDimPDE.jl/workflows/CI/badge.svg)](https://github.com/SciML/HighDimPDE.jl/actions?query=workflow%3ACI)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

# HighDimPDE.jl

**HighDimPDE.jl**は、**高次元の非局所的、非線形PDE**を解くためのJuliaパッケージです。形式は次の通りです。

:$

\begin{aligned} (\partial*t u)(t,x) &= \int*{\Omega} f\big(t,x,{\bf x}, u(t,x),u(t,{\bf x}), ( \nabla*x u )(t,x ),( \nabla*x u )(t,{\bf x} ) \big) d{\bf x} 
& \quad + \big\langle \mu(t,x), ( \nabla*x u )( t,x ) \big\rangle + \tfrac{1}{2} \text{Trace} \big(\sigma(t,x) [ \sigma(t,x) ]^* ( \text{Hess}*x u)(t, x ) \big). \end{aligned} :$

ここで、$u \colon [0,T] \times \Omega \to \mathbb{R}, \Omega \subseteq \mathbb{R}^{d}$は初期条件と境界条件に従い、$d$は大きいです。

## チュートリアルとドキュメント

パッケージの使用に関する情報は、[安定版のドキュメント](https://docs.sciml.ai/HighDimPDE/stable/)を参照してください。[開発中のドキュメント](https://docs.sciml.ai/HighDimPDE/dev/)は、未リリースの機能を含むドキュメントのバージョンです。

## インストール

Juliaを開いて、次のように入力します。

```julia
using Pkg;
Pkg.add("HighDimPDE.jl")
```

これにより、gitリポジトリから最新バージョンがダウンロードされ、すべての依存関係がダウンロードされます。

## 始め方

ドキュメントと`test`フォルダを参照してください。

## 参考文献

  * Boussange, V., Becker, S., Jentzen, A., Kuckuck, B., Pellissier, L., Deep learning approximations for non-local nonlinear PDEs with Neumann boundary conditions. [arXiv](https://arxiv.org/abs/2205.03672) (2022)

<!– - Becker, S., Braunwarth, R., Hutzenthaler, M., Jentzen, A., von Wurstemberger, P., Numerical simulations for full history recursive multilevel Picard approximations for systems of high-dimensional partial differential equations. [arXiv](https://arxiv.org/abs/2005.10206) (2020)

  * Beck, C., Becker, S., Cheridito, P., Jentzen, A., Neufeld, A., Deep splitting method for parabolic PDEs. [arXiv](https://arxiv.org/abs/1907.03452) (2019)
  * Han, J., Jentzen, A., E, W., Solving high-dimensional partial differential equations using deep learning. [arXiv](https://arxiv.org/abs/1707.02568) (2018) –>

<!– ## 謝辞 `HighDimPDE.jl`は、Sebastian BeckerのPython、TensorFlow、C++のスクリプトに触発されています。Arnulf Jentzen教授は、実装されたソルバーアルゴリズムの理論的発展に大きく貢献しました。 –>
