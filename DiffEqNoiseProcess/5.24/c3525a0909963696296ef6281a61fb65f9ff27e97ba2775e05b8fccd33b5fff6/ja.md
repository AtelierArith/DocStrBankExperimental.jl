多くの場合、解析解を持たない確率微分方程式によってノイズプロセスを直接定義したいと考えるでしょう。もちろん、これは分布的に正確ではなく、特性がどれだけ一致するかは微分方程式の統合の仕方に依存しますが、多くの場合、他の方法がはるかに難しいときに良い近似として使用できます。

`NoiseApproximation`は`DEIntegrator`によって定義されます。`NoiseApproximation`のコンストラクタは次のようになります。

```julia
NoiseApproximation(source1::DEIntegrator,
    source2::Union{DEIntegrator, Nothing} = nothing;
    reset = true)
```

`DEIntegrator`は、統合中に停止しないように、十分に遠い最終時間点を持っている必要があります。使いやすさのために、最終時間点を`Inf`として使用できます。時間点は将来の統合の時間点と一致する必要はなく、SDE解の補間関数が使用されるためです。したがって、制限要因は誤差許容度であり、特定の点に到達することではありません。

## NoiseApproximationの例

この例では、`NoiseApproximation`を使用して、確率微分方程式の定義から独自の幾何ブラウン運動を構築する方法を示します。通常の使用では、`GeometricBrownianMotionProcess`を使用するべきです。なぜなら、それがより効率的で分布的に正確だからです。

まず、`SDEProblem`を定義しましょう。ここでは、ノイズを無限の積分で使用できるように、時間範囲を`(0.0,Inf)`とします。

```julia
const μ = 1.5
const σ = 1.2
f(u, p, t) = μ * u
g(u, p, t) = σ * u
prob = SDEProblem(f, g, 1.0, (0.0, Inf))
```

次に、インテグレーターを構築し、そのインテグレーターを`NoiseApproximation`コンストラクタに送信することでノイズプロセスを構築します。

```julia
integrator = init(prob, SRIW1())
W = NoiseApproximation(integrator)
```

このノイズプロセスは、他のノイズプロセスと同様に使用できます。たとえば、今、ノイズプロセスが自体が幾何ブラウン運動である色付きノイズの幾何ブラウン運動を構築できます。

```julia
prob = SDEProblem(f, g, 1.0, (0.0, Inf), noise = W)
```

可能性は無限大です。
