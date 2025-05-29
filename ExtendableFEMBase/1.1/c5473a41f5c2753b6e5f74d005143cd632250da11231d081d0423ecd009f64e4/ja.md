```
ExtendableFEMBase
```

[![Build status](https://github.com/WIAS-PDELib/ExtendableFEMBase.jl/workflows/linux-macos-windows/badge.svg)](https://github.com/WIAS-PDELib/ExtendableFEMBase.jl/actions) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://wias-pdelib.github.io/ExtendableFEMBase.jl/stable/index.html) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://wias-pdelib.github.io/ExtendableFEMBase.jl/dev/index.html) [![DOI](https://zenodo.org/badge/667751152.svg)](https://zenodo.org/doi/10.5281/zenodo.10563410) [![code style: runic](https://img.shields.io/badge/code_style-%E1%9A%B1%E1%9A%A2%E1%9A%BE%E1>

# ExtendableFEMBase

このパッケージは、ExtendableGrids上で有限要素スキームを設定するための基本的な有限要素構造を提供します。完全な高レベルAPIについては、[ExtendableFEM.jl](https://github.com/WIAS-PDELib/ExtendableFEM.jl)を参照してください。

パッケージ内の低レベル構造には以下が含まれます：

  * 有限要素タイプ（参照幾何における基底関数と、いくつかのH1、HdivおよびHcurl要素のための自由度管理）
  * FESpace（ExtendableGridsからのメッシュに関する離散有限要素空間、Dofmapsを知っている）
  * FEMatrix（ExtendableSparse行列のためのブロックオーバーレイ、各ブロックはシステム内の2つのFESpace間の結合に対応）
  * FEVector（配列のためのブロックオーバーレイ、各ブロックはFESpaceに対応）
  * FunctionOperators（恒等、勾配、発散のような基本的な線形演算子）および異なる有限要素タイプに対してそれらを評価する方法のルール
  * FEEvaluator（異なるFunctionOperatorsおよびグリッドのエンティティに対する有限要素基底評価器）
  * QuadratureRule（ExtendableGridsからの異なるElementGeometriesのための基本的な数値積分ルール）
  * 補間（提供された有限要素空間への標準的な補間、平均化ルーチンおよびメッシュ/FESpace間の補間）
  * 再構成演算子（異なる有限要素タイプへの補間を含む特別なFunctionOperators）
