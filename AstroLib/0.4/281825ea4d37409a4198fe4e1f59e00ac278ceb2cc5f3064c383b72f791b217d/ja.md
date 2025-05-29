```
kepler_solver(M, e) -> E
```

### 目的

楕円運動領域 ($0 ≤ e ≤ 1$) におけるケプラーの方程式を解き、離心異常 $E$ を返します。

### 説明

与えられた時刻 $t$ における楕円運動の物体の位置を求めるためには、[ケプラーの方程式](https://en.wikipedia.org/wiki/Kepler%27s_equation) を解く必要があります。

$$
M(t) = E(t) - e \sin E(t)
$$

ここで、$M(t) = (t - t_0)/P$ は平均異常、$E(t)$ は離心異常、$e$ は軌道の離心率、$t_0$ は近日点通過の時刻、$P$ は軌道の周期です。通常、離心率は与えられ、特定の時刻 $t$ における離心異常 $E(t)$ を求めることが求められますので、平均異常 $M(t)$ も知られています。

### 引数

  * `M`: 平均異常。
  * `e`: 離心率、楕円運動領域において ($0 ≤ e ≤ 1$)

### 出力

離心異常 $E$、範囲は $[-π, π]$ に制限されます。

### 方法

ケプラーの方程式を解くためのさまざまな数値的手法が存在します。この関数は、Markley (1995) の Celestial Mechanics and Dynamical Astronomy, 63, 101 で提案されたアルゴリズムを実装しています (DOI:[10.1007/BF00691917](http://dx.doi.org/10.1007/BF00691917))。この方法は反復的ではなく、4回の超越関数の評価のみを必要とし、楕円運動の全範囲 $0 ≤ e ≤ 1$ において迅速かつ効率的であることが証明されています。

### 例

  * 離心率 $e = 0.7$ の軌道に対して、$M(t) = 8π/3$ の離心異常を求めます。

    ```jldoctest
    julia> using AstroLib

    julia> ecc = 0.7;

    julia> E = kepler_solver(8pi/3, ecc)
    2.5085279492864223
    ```
  * 離心率 $e = 0, 0.5, 0.9$ に対する平均異常の関数としての離心異常をプロットします。`kepler_solver` は $E ∈ [-π, π]$ を返すので、$[0, 2π]$ にするために `mod2pi` を使用します。プロットには [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) を使用します。

    ```julia
    using AstroLib
    using Plots
    M = range(0, stop=2pi, length=1001)[1:end-1];
    for ecc in (0, 0.5, 0.9)
        plot(M, mod2pi.(kepler_solver.(M, ecc)))
    end
    ```

### 注意

真異常は `trueanom` 関数を使用して計算できます。
