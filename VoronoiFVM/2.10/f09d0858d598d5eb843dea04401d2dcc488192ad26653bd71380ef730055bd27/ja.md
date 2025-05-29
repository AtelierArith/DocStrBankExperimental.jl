```
VoronoiFVM
```

# VoronoiFVM.jl

[![Build status](https://github.com/WIAS-PDELib/VoronoiFVM.jl/actions/workflows/ci.yml/badge.svg?branch=master)](https://github.com/WIAS-PDELib/VoronoiFVM.jl/actions/workflows/ci.yml?query=branch%3Amaster) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://WIAS-PDELib.github.io/VoronoiFVM.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://WIAS-PDELib.github.io/VoronoiFVM.jl/dev) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3529808.svg)](https://doi.org/10.5281/zenodo.3529808) [![Zulip Chat](https://img.shields.io/badge/zulip-join_chat-brightgreen.svg)](https://julialang.zulipchat.com/#narrow/stream/379007-voronoifvm.2Ejl) [![code style: runic](https://img.shields.io/badge/code_style-%E1%9A%B1%E1%9A%A2%E1%9A%BE%E1%9B%81%E1%9A%B2-black)](https://github.com/fredrikekre/Runic.jl)

Voronoi有限体積法に基づく、結合非線形偏微分方程式（楕円-放物線保存則）のソルバーです。ユーザ関数とそのヤコビアンを評価し、解のパラメータに対する導関数を計算するために、[ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)および[DiffResults.jl](https://github.com/JuliaDiff/DiffResults.jl)を介して自動微分を使用します。

## JuliaCon 2024 ライトニングトーク: [要旨](https://pretalx.com/juliacon2024/talk/F9FBWD/), [ビデオ](https://www.youtube.com/watch?v=v0RPD4eSzVE&t=5120s)

## 最近の変更

最近の[変更](https://WIAS-PDELib.github.io/VoronoiFVM.jl/stable/changes)のリストを確認してください。

## 付随パッケージ

  * [ExtendableSparse.jl](https://github.com/WIAS-PDELib/ExtendableSparse.jl): 便利で効率的なスパース行列のアセンブリ
  * [ExtendableGrids.jl](https://github.com/WIAS-PDELib/ExtendableGrids.jl): 非構造化グリッド管理ライブラリ
  * [SimplexGridFactory.jl](https://github.com/WIAS-PDELib/SimplexGridFactory.jl): 統一された高レベルメッシュジェネレーターインターフェース
  * [Triangulate.jl](https://github.com/JuliaGeometry/Triangulate.jl): J. Shewchukによる[Triangle](https://www.cs.cmu.edu/~quake/triangle.html)三角メッシュジェネレーターのJuliaラッパー
  * [TetGen.jl](https://github.com/JuliaGeometry/TetGen.jl): H. Siによる[TetGen](http://www.tetgen.org)四面体メッシュジェネレーターのJuliaラッパー
  * [GridVisualize.jl](https://github.com/WIAS-PDELib/GridVisualize.jl): ExtendableGrids.jlに関連するグリッドと関数の視覚化
  * [PlutoVista.jl](https://github.com/j-fu/PlutoVista.jl): Plutoノートブックで使用するための[GridVisualize.jl](https://github.com/WIAS-PDELib/GridVisualize.jl)のバックエンド

VoronoiFVM.jlとこれらのパッケージのほとんどは、メタパッケージ[PDELib.jl](https://github.com/WIAS-PDELib/PDELib.jl)の一部です。

## いくつかの代替案

  * [ExtendableFEM.jl](https://github.com/chmerdon/ExtendableFEM.jl): Ch. Merdonによる同じパッケージベースからの勾配ロバストFEMを実装した有限要素ライブラリ
  * [SkeelBerzins.jl](https://github.com/gregoirepourtier/SkeelBerzins.jl): Matlabの`pdepe` APIのジュリア版
  * [Trixi.jl](https://github.com/trixi-framework/Trixi.jl): ハイパーボリック保存則の数値シミュレーションフレームワーク
  * [GridAP.jl](https://github.com/gridap/Gridap.jl) Juliaにおける偏微分方程式のグリッドベースの近似
  * [Ferrite.jl](https://github.com/Ferrite-FEM/Ferrite.jl) Juliaの有限要素ツールボックス
  * [FinEtools.jl](https://github.com/PetrKryslUCSD/FinEtools.jl) Juliaの有限要素ツール
  * [FiniteVolumeMethod.jl](https://github.com/DanielVandH/FiniteVolumeMethod.jl/) [Donald boxes](https://sciml.github.io/FiniteVolumeMethod.jl/dev/math/#Control-volumes)を用いた有限体積法

## VoronoiFVM.jlを使用しているいくつかのプロジェクトとパッケージ

  * [ChargeTransport.jl: 半導体デバイスのドリフト拡散シミュレーター](https://github.com/PatricioFarrell/ChargeTransport.jl)
  * [LiquidElectrolytes.jl: 液体電解質の一般化されたネルンスト-プランク-ポアソンモデル](https://github.com/j-fu/LiquidElectrolytes.jl)
  * [MultiComponentReactiveMixtureProject: 多孔質媒体における熱と多成分反応性気体相輸送のモデル。](https://github.com/DavidBrust/MultiComponentReactiveMixtureProject)
  * [RfbScFVM: フローバッテリーセルの性能予測](https://github.com/Isomorph-Electrochemical-Cells/RfbScFVM)
  * [MosLab.jl: 半導体からトランジスタレベルのモデリングをJuliaで](https://github.com/Rapos0/MOSLab.jl)

## 引用

このパッケージをあなたの作業で使用する場合は、[CITATION.cff](https://raw.githubusercontent.com/WIAS-PDELib/VoronoiFVM.jl/master/CITATION.cff)に従って引用してください。
