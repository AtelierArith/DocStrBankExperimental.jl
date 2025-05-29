# アクチンリングモンテカルロシミュレーションパッケージ

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://cumberworth.github.io/ActinRingsMC.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://cumberworth.github.io/ActinRingsMC.jl/dev) [![Build Status](https://github.com/cumberworth/ActinRingsMC.jl/actions/workflows/CI.yml/badge.svg?branch=master)](https://github.com/cumberworth/ActinRingsMC.jl/actions/workflows/CI.yml?query=branch%3Amaster) [![Coverage](https://codecov.io/gh/cumberworth/ActinRingsMC.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/cumberworth/ActinRingsMC.jl) [![DOI](https://zenodo.org/badge/420141493.svg)](https://zenodo.org/badge/latestdoi/420141493)

アダプティブアンブレラサンプリングモンテカルロシミュレーションのための関数を持つJuliaシミュレーションパッケージで、架橋されたアクチンリングのシミュレーションを実行します。

[リポジトリ](https://github.com/cumberworth/ActinRingsMC.jl)

[ドキュメント](http://www.cumberworth.org/ActinRingsMC.jl)

このパッケージは、[Ref. 1](#references)の補足資料に概説されたシミュレーションプロトコルを実装しています。

## インストール

パッケージは、Julia REPLを起動し、`]`を入力してパッケージモードに入り、次のコマンドを実行することでインストールできます。

```
add ActinRingsMC
```

一般レジストリからインストールするか、次のコマンドを実行して開発リポジトリから直接インストールできます。

```
add https://github.com/cumberworth/ActinRingsMC.jl
```

## シミュレーションの実行

リポジトリの`examples`ディレクトリには、アンブレラサンプリング用のスクリプトがあります。初回実行と継続実行の両方があります。コマンドはJulia REPLで実行するか、スクリプトと同じディレクトリにいる場合は次のように実行できます。

```
julia run-umbrella-sampling.jl
```

良好なサンプリングを達成するためには、イテレーションごとのステップ数とイテレーション数を試行する必要があります。

## 分析と視覚化

シミュレーションは、シミュレーションごとに2種類のデータファイルを出力します。アンブレラサンプリング実行の場合は、イテレーションごとに出力されます。`.ops`拡張子のファイルタイプには、書き込み間隔によって決定されたステップで保存された順序パラメータが含まれており、分析とプロットのためにデータフレームとして読み込むことができます。現在、順序パラメータにはエネルギー、格子の高さ、リングの半径が含まれています。`.vtf`拡張子のファイルタイプは、分子視覚化プログラム[ VMD](https://www.ks.uiuc.edu/Research/vmd/)によって読み取ることができ、シミュレーションの構成を空間的に視覚化できます。VMDで表示する際は、「Coloring Method」に「Chain」を、「Drawing Method」に「VDW」を使用することをお勧めします。シミュレーションは、実行に使用されたすべてのシステムおよびシミュレーションパラメータを含むファイルを`.parms`ファイルに出力します。

アンブレラサンプリング実行は、追加のファイルタイプを出力します。これらのファイルの出力は、書き込み頻度によって決定されたものだけでなく、すべてのステップに基づいています。最上行には格子の高さ（またはビン、ただしビニングはテストされていません）が表示されます。各次の行にはイテレーションからのデータが含まれています。`.counts`は各格子の高さが訪れた回数を示し、`.freqs`はその正規化バージョンを示します。`.biases`には、そのイテレーションに使用されたバイアスが含まれています（そのデータから計算されるものとは対照的です）。

関連するPythonパッケージ[actinrings](https://github.com/cumberworth/actinrings)には、これらのシミュレーションからの出力を分析およびプロットするためのコードが含まれており、自由エネルギーやリング収縮力を含みます。詳細についてはそのドキュメントを参照してください。

## 参考文献

[1] A. Cumberworth and P. R. t. Wolde, アクチンリングの収縮に関する受動的架橋剤による。

## リンク

[Juliaプログラミング言語](https://julialang.org/)

[再現分析パッケージ](https://github.com/cumberworth/actinrings)

[VMD](https://www.ks.uiuc.edu/Research/vmd/)

  * [`Lattice`](@ref)
  * [`SimulationParams`](@ref)
  * [`System`](@ref)
  * [`SystemParams`](@ref)
  * [`calc_Lf`](@ref)
  * [`calc_lf`](@ref)
  * [`calc_max_lattice_height`](@ref)
  * [`calc_min_lattice_height`](@ref)
  * [`calc_radius`](@ref)
  * [`generate_starting_config`](@ref)
  * [`run!`](@ref)
  * [`run_us!`](@ref)
  * [`update_occupancies!`](@ref)
