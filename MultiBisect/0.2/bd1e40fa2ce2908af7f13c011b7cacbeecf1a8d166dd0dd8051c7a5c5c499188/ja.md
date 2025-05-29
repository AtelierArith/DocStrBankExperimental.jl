```
bisect(f, grid; threaded=false, monotonic=false, iterations=5, verbose=false)
```

初期の評価点の `grid` 上で関数 `f` の多次元二分法アルゴリズムを実行します。

# 引数

## 位置引数

  * `f`: 評価される関数
  * `grid`: 初期評価グリッドを記述する範囲のタプル

## キーワード引数

  * `threaded`: マルチスレッド評価のために `true` に設定
  * `monotonic`: `f` が各次元で単調であることが知られている場合は `true` に設定
  * `iterations`: アルゴリズムを繰り返す回数
  * `verbose`: 各イテレーションでの新しい関数評価の数を印刷するために `true` に設定

# 例

```jldoctest
julia> grid = (0.0:1.0, 0.0:1.0);

julia> bisect(x -> 1 - sum(abs2, x), grid)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> x[2] - x[1], grid)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> x[2] - x[1], grid; monotonic=true)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 67
        Edges: 32
```

# 拡張ヘルプ

## アルゴリズム

アルゴリズムは、$N$ 次元のハイパーキューブ（線、正方形、立方体など）の初期評価グリッドから始まり、各段階で「半分」に分割しますが、関数が符号を変えることが知られている領域のみで行います。関数が評価された後、各ハイパーキューブは半分に分割され（線は2本に、正方形は4つに、立方体は8つに）、各頂点での関数の符号がチェックされます。すべての頂点が同じ符号を持たない場合、関数はハイパーキューブ内のどこかで符号を変える必要があるため、サブキューブの頂点（例えば、線の中点）が次の段階で評価のためにマークされます。すべての頂点が同じ符号を持つ場合、関数はハイパーキューブ全体で同じ符号を持つと推定されるため、内部のすべての点で符号が推測され、ハイパーキューブ内で関数は再評価されません。

キーワード `monotonic=true` を渡すことで、アルゴリズムはさらに、関数が同じ符号を持つ2点間の任意の方向で符号を変えることができないと仮定します。これは、ハイパーキューブの各辺の頂点で関数の符号をチェックする必要があることを意味します。符号が同じであれば、関数は辺に沿った中点でも同じ符号を持つと仮定され、評価されません。

## マルチスレッド

キーワード引数 `threaded=true` を設定すると、各イテレーションでの関数の評価がマルチスレッドになります。評価が非常に安価な関数の場合、スレッドのセットアップからのオーバーヘッドが実際に各イテレーションを長くします。ただし、この効果はすぐに消えます。

### 例

```julia-repl
julia> ffast(x) = 1 - sum(abs2, x);

julia> grid = (0.0:1.0, 0.0:1.0);

julia> @btime bisect(ffast, $grid; threaded=false);
  49.720 μs (40 allocations: 3.59 KiB)

julia> @btime bisect(ffast, $grid; threaded=true);
  146.173 μs (163 allocations: 18.23 KiB)

julia> fslow(x) = (sleep(0.1); ffast(x))
fslow (generic function with 1 method)

julia> @btime bisect(fslow, $grid; threaded=false);
  11.397 s (605 allocations: 20.83 KiB)

julia> @btime bisect(fslow, $grid; threaded=true);
  3.170 s (736 allocations: 35.45 KiB)
```

## 単調性

関数 `f` が単調であることが知られている場合、両方の頂点が同じ符号を持つ辺に沿った `f` の挙動を推測することで評価の数を減らすことができます。

### 例

```jldoctest
julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); monotonic=false)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); monotonic=true)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 80
        Edges: 32
```

## イテレーション

より細かいグリッドの場合、アルゴリズムをより多くのイテレーションで繰り返します。

### 例

```jldoctest
julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0))
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); iterations=3)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.25:1.0, 0.0:0.25:1.0)
  Grid points: 25
  Evaluations: 22
        Edges: 8


julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); iterations=7)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.015625:1.0, 0.0:0.015625:1.0)
  Grid points: 4225
  Evaluations: 490
        Edges: 128
```

## ロギング

長時間実行される二分法の場合、新しい評価の数をスレッドセーフな進捗メーターの一種として報告することが有用です。

### 例

```jldoctest
julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); verbose=true)
[ Info: Iteration 1: 4 gridpoints (4 evaluations)
[ Info: Iteration 2: 9 gridpoints (5 evaluations)
[ Info: Iteration 3: 25 gridpoints (13 evaluations)
[ Info: Iteration 4: 81 gridpoints (29 evaluations)
[ Info: Iteration 5: 289 gridpoints (61 evaluations)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); verbose=true, iterations=7)
[ Info: Iteration 1: 4 gridpoints (4 evaluations)
[ Info: Iteration 2: 9 gridpoints (5 evaluations)
[ Info: Iteration 3: 25 gridpoints (13 evaluations)
[ Info: Iteration 4: 81 gridpoints (29 evaluations)
[ Info: Iteration 5: 289 gridpoints (61 evaluations)
[ Info: Iteration 6: 1089 gridpoints (125 evaluations)
[ Info: Iteration 7: 4225 gridpoints (253 evaluations)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.015625:1.0, 0.0:0.015625:1.0)
  Grid points: 4225
  Evaluations: 490
        Edges: 128
```
