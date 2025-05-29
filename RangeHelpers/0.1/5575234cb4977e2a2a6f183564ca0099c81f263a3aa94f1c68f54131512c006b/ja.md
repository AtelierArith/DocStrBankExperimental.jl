# RangeHelpers

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://jw3126.github.io/RangeHelpers.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://jw3126.github.io/RangeHelpers.jl/dev) [![Build Status](https://github.com/jw3126/RangeHelpers.jl/workflows/CI/badge.svg)](https://github.com/jw3126/RangeHelpers.jl/actions) [![Build Status](https://travis-ci.com/jw3126/RangeHelpers.jl.svg?branch=master)](https://travis-ci.com/jw3126/RangeHelpers.jl) [![Coverage](https://codecov.io/gh/jw3126/RangeHelpers.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/jw3126/RangeHelpers.jl)

開始点が10、終了点が121.7、ステップが25の範囲が必要だったことはありませんか？それは数学的に不可能なので、妥協が必要です。多くの選択肢がありますが、開始点、終了点、またはステップを緩和することができます。過去には、これを行うのは面倒で、オフバイワンエラーを引き起こす可能性がありました：

```jldoctest README
julia> Base.range(10, step=25, length=round(Int, (121.7-10)/25)); # 正しいですか？？
```

[RangeHelpers.jl](https://github.com/jw3126/RangeHelpers.jl)は、範囲構築の頭痛を一度で解決することを目指しています：

```jldoctest README
julia> using RangeHelpers: range

julia> using RangeHelpers

julia> range(start = 10, stop = 121.7, step = around(25)) # ステップで妥協
10.0:27.925:121.7

julia> range(start = 10, stop = 121.7, step = ≤(25))  # ステップを最大25で妥協
10.0:22.34:121.7

julia> range(start = 10, stop = ≥(121.7), step = 25)  # 正確なステップだが、より大きな終了点を許可
10:25:135

julia> anchorrange(42, start = around(10), step = 25, stop = around(121.7)) # 42がグリッド上にあることを確認
17:25:117
```

さらに多くの範囲を作成する方法については、[ドキュメント](https://jw3126.github.io/RangeHelpers.jl/dev/)を参照してください。
