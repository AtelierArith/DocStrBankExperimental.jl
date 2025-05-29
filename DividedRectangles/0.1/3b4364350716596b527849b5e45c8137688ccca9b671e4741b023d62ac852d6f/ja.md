```
optimize(f, a::Vector{Float64}, b::Vector{Float64}; max_iterations::Int = 100, min_radius::Float64 = 1e-5)
```

DividedRectanglesモジュールの主要な最適化ルーチンです。これは、`a`と`b`によって定義された制約された探索空間における目的関数`f`のグローバル最小値を検索するためにDIRECTアルゴリズムを使用します。

# 引数

  * `f`: 最小化される目的関数。ℝⁿの入力に対して定義されている必要があります。
  * `a::Vector{Float64}`: 探索空間の下限のベクトル。
  * `b::Vector{Float64}`: 探索空間の上限のベクトル。
  * `max_iterations::Int`: (オプション) DIRECTアルゴリズムの最大反復回数（デフォルトは100）。
  * `min_radius::Float64`: (オプション) ハイパーレクタングルがもはや細分化されない最小半径（デフォルトは1e-5）。

# 戻り値

  * DIRECTアルゴリズムによって見つかった最良の設計（すなわち、元の探索空間における点）を表す`Float64`のベクトル。
