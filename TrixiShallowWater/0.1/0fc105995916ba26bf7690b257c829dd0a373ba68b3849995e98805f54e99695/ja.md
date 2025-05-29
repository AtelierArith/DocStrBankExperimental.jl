```
ShallowWaterEquationsWetDry2D(; gravity, H0 = 0, threshold_limiter = nothing, threshold_wet = nothing)
```

二次元空間における浅水方程式（SWE）。方程式は次のように与えられます。

$$
\begin{aligned}
  \frac{\partial h}{\partial t} + \frac{\partial}{\partial x}(h v_1)
    + \frac{\partial}{\partial y}(h v_2) &= 0 \\
    \frac{\partial}{\partial t}(h v_1) + \frac{\partial}{\partial x}\left(h v_1^2 + \frac{g}{2}h^2\right)
    + \frac{\partial}{\partial y}(h v_1 v_2) + g h \frac{\partial b}{\partial x} &= 0 \\
    \frac{\partial}{\partial t}(h v_2) + \frac{\partial}{\partial x}(h v_1 v_2)
    + \frac{\partial}{\partial y}\left(h v_2^2 + \frac{g}{2}h^2\right) + g h \frac{\partial b}{\partial y} &= 0.
\end{aligned}
$$

SWEの未知数は水の高さ $h$ と速度 $\mathbf{v} = (v_1, v_2)^T$ です。重力加速度は `g` で示され、（おそらく）変動する底面地形関数 $b(x,y)$ です。保存変数である水の高さ $h$ は底面地形 $b$ から測定されるため、全水深 $H = h + b$ も定義されます。

追加の量 $H_0$ は、初期条件を設定したり「静止湖」の良好なバランスをテストするのに役立つ全水深の参照値を格納するために利用可能です。

また、数値的な問題や不安定性を防ぐための4つの閾値があります。これらの閾値はすべて通過する必要はなく、デフォルト値が構造体内で定義されています。最初の `threshold_limiter` は、水の高さに対して [`PositivityPreservingLimiterShallowWater`](@ref) で使用され、初期条件に対する（小さな）シフトと次の時間ステップの前にカットオフされます。2つ目の `threshold_wet` は、水の高さに適用され、数値フラックスを計算する前に流れが「湿っている」かどうかを定義します。3つ目の `threshold_partially_wet` は、水の高さに適用され、[`IndicatorHennemannGassnerShallowWater`](@ref) で「部分的に湿った」要素を定義し、それらは純粋なFV法で計算されて良好なバランスを確保します。最後に、`threshold_desingularization` は、速度の非特異化手続きのために [`PositivityPreservingLimiterShallowWater`](@ref) で使用されます。`Float64` では閾値を通過する必要はなく、デフォルト値が構造体内で定義されています。他の数値形式では `threshold_partially_wet` を提供する必要があります。

底面地形関数 $b(x,y)$ は、特定の問題設定の初期条件ルーチン内で設定されます。SWEの保存形式をテストするために、底面地形変数 `b` をゼロに設定することができます。

未知数に加えて、TrixiShallowWater.jl は現在、時間的に固定されているにもかかわらず、近似点での底面地形値を格納しています。これは、近似中に底面地形の勾配を即座に計算する便利さや、全水深 $H$ やエントロピー変数のような補助量を計算するために行われます。これにより、これらの方程式の実装と使用にさまざまな影響があります：

  * 底面地形に対応するフラックス値はゼロでなければなりません。
  * 初期条件、境界条件、またはソース項を定義する際に底面地形値を含める必要があります。
  * [`Trixi.AnalysisCallback`](@extref) はこの変数を分析します。
  * Trixi.jl の視覚化ツールは、デフォルトで底面地形を視覚化します。

SWEに関する参考文献は多くありますが、良い入門書は次の書籍の第13章にあります：

  * Randall J. LeVeque (2002) Finite Volume Methods for Hyperbolic Problems [DOI: 10.1017/CBO9780511791253](https://doi.org/10.1017/CBO9780511791253)
