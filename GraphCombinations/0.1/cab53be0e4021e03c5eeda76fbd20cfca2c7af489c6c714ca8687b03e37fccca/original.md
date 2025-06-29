# GraphCombinations.jl

[![docs](https://img.shields.io/badge/docs-online-blue.svg)](https://oameye.github.io/GraphCombinations.jl/) [![codecov](https://codecov.io/gh/oameye/GraphCombinations.jl/branch/main/graph/badge.svg)](https://app.codecov.io/gh/oameye/GraphCombinations.jl) [![Benchmarks](https://github.com/oameye/GraphCombinations.jl/actions/workflows/Benchmarks.yaml/badge.svg?branch=main)](https://oameye.github.io/GraphCombinations.jl/benchmarks/)

[![Code Style: Blue](https://img.shields.io/badge/blue%20style%20-%20blue-4495d1.svg)](https://github.com/JuliaDiff/BlueStyle) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl) [![jet](https://img.shields.io/badge/%F0%9F%9B%A9%EF%B8%8F_tested_with-JET.jl-233f9a)](https://github.com/aviatesk/JET.jl) [![DispatchDoctor](https://img.shields.io/badge/%F0%9F%A9%BA_tested_with-DispatchDoctor.jl-blue?labelColor=white)](https://github.com/MilesCranmer/DispatchDoctor.jl)

GraphCombinations.jl is a package for the generation of graphs for a given set of different vertices. Given a set of [valent vertices](https://en.wikipedia.org/wiki/Degree_%28graph_theory%29) (vertices of degree k), the package generates all possible graphs that can be constructed with these vertices.

The implementation is rather naive and I am sure it can be significiantly improved. Any contributions or suggestions are welcome :)

This package is heavily inspired by this [StackExachange post](https://mathematica.stackexchange.com/questions/170268/how-to-generate-all-feynman-diagrams-with-mathematica) by AccidentalFourierTransform. A mathematica notebook using his code can be found in the [examples folder](https://github.com/oameye/GraphCombinations.jl/tree/main/examples). 
