# RecursiveArrayTools.jl

[![Join the chat at https://julialang.zulipchat.com #sciml-bridged](https://img.shields.io/static/v1?label=Zulip&message=chat&color=9558b2&labelColor=389826)](https://julialang.zulipchat.com/#narrow/stream/279055-sciml-bridged) [![Global Docs](https://img.shields.io/badge/docs-SciML-blue.svg)](https://docs.sciml.ai/RecursiveArrayTools/stable/)

[![codecov](https://codecov.io/gh/SciML/RecursiveArrayTools.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/SciML/RecursiveArrayTools.jl) [![Build Status](https://github.com/SciML/RecursiveArrayTools.jl/workflows/CI/badge.svg)](https://github.com/SciML/RecursiveArrayTools.jl/actions?query=workflow%3ACI) [![build status](https://badge.buildkite.com/9eab94781cf0af9a3566e9b9f16abe5aea167b640b88065285.svg?branch=master)](https://buildkite.com/julialang/recursivearraytools-dot-jl)

[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%27s%20Guide-blueviolet)](https://github.com/SciML/ColPrac) [![SciML Code Style](https://img.shields.io/static/v1?label=code%20style&message=SciML&color=9558b2&labelColor=389826)](https://github.com/SciML/SciMLStyle)

RecursiveArrayTools.jlは、配列の配列のような再帰的配列を扱うためのツールのセットです。

## チュートリアルとドキュメント

パッケージの使用に関する情報は、[安定版のドキュメント](https://docs.sciml.ai/RecursiveArrayTools/stable/)を参照してください。[開発中のドキュメント](https://docs.sciml.ai/RecursiveArrayTools/dev/)は、未リリースの機能を含むドキュメントのバージョンです。

## 例

```julia
using RecursiveArrayTools
a = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
b = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
vA = VectorOfArray(a)
vB = VectorOfArray(b)

vA .* vB # これで標準的な配列の操作がすべて機能します！

a = (rand(5), rand(5))
b = (rand(5), rand(5))
pA = ArrayPartition(a)
pB = ArrayPartition(b)

pA .* pB # これで標準的な配列の操作がすべて機能します！
```
