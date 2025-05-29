# GraphCombinations.jl

[![docs](https://img.shields.io/badge/docs-online-blue.svg)](https://oameye.github.io/GraphCombinations.jl/) [![codecov](https://codecov.io/gh/oameye/GraphCombinations.jl/branch/main/graph/badge.svg)](https://app.codecov.io/gh/oameye/GraphCombinations.jl) [![Benchmarks](https://github.com/oameye/GraphCombinations.jl/actions/workflows/Benchmarks.yaml/badge.svg?branch=main)](https://oameye.github.io/GraphCombinations.jl/benchmarks/)

[![Code Style: Blue](https://img.shields.io/badge/blue%20style%20-%20blue-4495d1.svg)](https://github.com/JuliaDiff/BlueStyle) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl) [![jet](https://img.shields.io/badge/%F0%9F%9B%A9%EF%B8%8F_tested_with-JET.jl-233f9a)](https://github.com/aviatesk/JET.jl) [![DispatchDoctor](https://img.shields.io/badge/%F0%9F%A9%BA_tested_with-DispatchDoctor.jl-blue?labelColor=white)](https://github.com/MilesCranmer/DispatchDoctor.jl)

GraphCombinations.jlは、異なる頂点のセットに対してグラフを生成するためのパッケージです。与えられた[バレント頂点](https://en.wikipedia.org/wiki/Degree_%28graph_theory%29)（次数kの頂点）のセットに基づいて、このパッケージはこれらの頂点を使用して構築できるすべての可能なグラフを生成します。

実装はかなり単純であり、かなりの改善が可能であると確信しています。貢献や提案は大歓迎です :)

このパッケージは、AccidentalFourierTransformによるこの[StackExachangeの投稿](https://mathematica.stackexchange.com/questions/170268/how-to-generate-all-feynman-diagrams-with-mathematica)に大きく触発されています。彼のコードを使用したMathematicaノートブックは、[examplesフォルダ](https://github.com/oameye/GraphCombinations.jl/tree/main/examples)にあります。
