# 線形補間

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://jw3126.github.io/LinearInterpolations.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://jw3126.github.io/LinearInterpolations.jl/dev) [![Build Status](https://github.com/jw3126/LinearInterpolations.jl/workflows/CI/badge.svg)](https://github.com/jw3126/LinearInterpolations.jl/actions)

# なぜ？

Juliaには補間のための優れたパッケージが多数あります。例えば：

  * [Interpolations.jl](https://github.com/JuliaMath/Interpolations.jl)
  * [Dierckx.jl](https://github.com/kbarbary/Dierckx.jl)
  * [GridInterpolations.jl](https://github.com/sisl/GridInterpolations.jl)

私が知っているすべてのパッケージは、補間されるオブジェクトが加算とスカラー乗算を実装していることを前提としています。しかし、数学的には線形補間には加重平均の概念だけが必要です。加重平均をサポートするが加算および/またはスカラー乗算をサポートしないオブジェクトの例は次のとおりです：

  * 確率分布
  * 回転およびさまざまな他のリー群

このパッケージは、任意の加重平均の概念で動作します。

# 使用法

```jldoctest README
julia> using LinearInterpolations

julia> xs = 1:3; ys=[10, 100, 1000]; # 1次元

julia> interpolate(xs, ys, 1)
10.0

julia> interpolate(xs, ys, 1.5)
55.0

julia> pt = [1.5]; interpolate(xs, ys, pt)
55.0

julia> itp = Interpolate(xs, ys); # 便利のために呼び出し可能なものを構築

julia> itp(1.5)
55.0

julia> grid=(1:3, [10, 15]); vals = [1 2; 3 4; 5 6]; pt=[1,10]; # 多次元

julia> interpolate(grid, vals, pt)
1.0

julia> function winner_takes_it_all(wts, objs)
    # 加重平均のカスタム概念
    I = argmax(wts)
    return objs[I]
end

julia> xs = 1:4; ys=[:no, :addition, :or, :multiplication];

julia> interpolate(xs, ys, 1.1, combine=winner_takes_it_all)
:no

julia> interpolate(xs, ys, 1.9, combine=winner_takes_it_all)
:addition

julia> interpolate(xs, ys, 3.7, combine=winner_takes_it_all)
:multiplication
```

# 設計目標

  * 軽量でシンプル
  * `+,*`を定義しないオブジェクトの補間をサポート
  * 妥当なパフォーマンス
