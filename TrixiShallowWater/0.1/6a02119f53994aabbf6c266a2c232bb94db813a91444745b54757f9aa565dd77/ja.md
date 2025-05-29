```
ShallowWaterMultiLayerEquations1D(gravity, H0, rhos)
```

多層浅水方程 (MLSWE) の1次元空間における方程式は次のように与えられます。

$$
\left\{
	\begin{aligned}			
		&\partial_t h_m + \partial_x h_mv_m = 0,\\
		&\partial h_mv_m + \partial_x h_mv_m^2 = -gh_m\partial_x \bigg(b + \sum\limits_{k\geq j}h_k + \sum\limits_{k<m}\frac{\rho_k}{\rho_m}h_k \bigg)
	\end{aligned}
\right.
$$

ここで、$m = 1, 2, ..., M$ は層のインデックスで、未知の変数は水の高さ $h$ と速度 $v$ です。さらに、$g$ は重力加速度、$b(x)$ は底面の地形、$\rho_m$ は m 番目の層の密度を示し、異なる層が上から下に向かって密度が増加するように $\rho_1 < \rho_2 < ... < \rho_M$ となるように選ばれなければなりません。

我々は、圧力項を非保守項として再定式化した特定の系の定式化を使用しており、これは良好なバランスのスキームの設計にいくつかの利点があります。

追加の量 $H_0$ は、初期条件を設定したり「静止湖」の良好なバランスをテストするのに役立つ総水高さの参照値を格納するために利用可能です。

また、数値的な問題や不安定性を防ぐための2つの閾値があります。リミッターは水の高さに対して [`PositivityPreservingLimiterShallowWater`](@ref) で使用されます。`threshold_limiter` は初期条件に対する（小さな）シフトとして機能し、次の時間ステップの前にカットオフされます。一方、`threshold_desingularization` は速度のデシンギュラリゼーションに使用されます。3つ目の `threshold_partially_wet` は水の高さに適用され、[`IndicatorHennemannGassnerShallowWater`](@ref) で「部分的に湿った」要素を定義し、これらは純粋な FV メソッドで計算されて良好なバランスを確保します。`Float64` では閾値を渡す必要はなく、デフォルト値が構造体内で定義されています。他の数値形式では `threshold_desingularization` と `threshold_partially_wet` を提供する必要があります。

底面の地形関数 $b(x)$ は、特定の問題設定の初期条件ルーチン内で設定されます。

未知数に加えて、Trixi は現在、時間的に固定されているにもかかわらず、近似点での底面の地形値を格納しています。これは、近似中に底面の地形勾配を即座に計算する便利さや、総水高さ $H$ やエントロピー変数のような補助量を計算するために行われています。これにより、これらの方程式の実装と使用にさまざまな影響があります：

  * 底面の地形に対応するフラックス値はゼロでなければなりません。
  * 初期条件、境界条件、またはソース項を定義する際に底面の地形値を含める必要があります。
  * [`Trixi.AnalysisCallback`](@extref) はこの変数を分析します。
  * Trixi の視覚化ツールはデフォルトで底面の地形を視覚化します。

MLSWE の良い入門書は、次の書籍の第12章で入手できます：

  * Benoit Cushman-Roisin (2011) 地球物理流体力学への入門：物理的および数値的側面 [https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C](https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C) ISBN: 978-0-12-088759-0

```
