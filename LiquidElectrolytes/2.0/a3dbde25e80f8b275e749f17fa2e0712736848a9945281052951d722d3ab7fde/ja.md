[![linux-macos-windows](https://github.com/j-fu/LiquidElectrolytes.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/j-fu/LiquidElectrolytes.jl/actions/workflows/ci.yml) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://j-fu.github.io/LiquidElectrolytes.jl/dev) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://j-fu.github.io/LiquidElectrolytes.jl/stable)

# LiquidElectrolytes.jl

このパッケージは、有限イオンサイズ、溶媒和、電気浸透圧を考慮した一般化ポアソン-ネルンスト-プランクモデルのソルバーです。これは、[非平衡熱力学の第一原理から導出された定式化](https://doi.org/10.1016/j.elecom.2014.03.015)に基づいています。電気静電ポテンシャルと過剰化学ポテンシャルの和を対流項として使用する[熱力学的一貫性のある有限体積空間離散化アプローチ](https://doi.org/10.1007/s00211-022-01279-y)を利用しています。これは、[ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)を活用して、離散非線形システムの堅牢なニュートンソルバーの基礎として、結合非線形PDEシステムの完全な線形化を生成するソルバーカーネル[VoronoiFVM.jl](https://github.com/WIAS-PDELib/VoronoiFVM.jl)の上に実現されています。

パッケージの一部はまだ進行中です。
