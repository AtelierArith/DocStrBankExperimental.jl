```julia
NoiseTransport{T, N, wType, zType, Tt, T2, T3, TRV, Trv, RNGType, inplace} <:
AbstractNoiseProcess{T, N, nothing, inplace}
```

これにより、`W(t) = f(u, p, t, RV)`の形の確率過程を定義できます。ここで、`f`は関数であり、`RV`はランダム変数を表します。これは関数を遅延評価で使用し、関数呼び出しを最小限に抑えるために必要な値のみをキャッシュしますが、全体のノイズ配列を保存することはありません。これには、`W`の定義域内の初期時点`t0`が必要です。望ましいSDEアルゴリズムが複数のプロセスを必要とする場合は、2つ目の関数が必要です。

```julia
NoiseTransport{iip}(t0,
    W,
    RV,
    rv,
    Z = nothing;
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true,
    reseed = true,
    noise_prototype = W(nothing, nothing, t0, rv)) where {iip}
```

```julia
NoiseTransport(t0,
    W,
    RV;
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true,
    reseed = true,
    kwargs...)
```

さらに、より効率的に多次元プロセスの配列を生成するために、インプレース関数`W(out, u, p, t, rv)`を使用できます。インプレースバージョンがアウトオブプレースバージョンのディスパッチなしで使用される場合、`noise_prototype`を設定する必要があります。

## NoiseTransportの例

`NoiseTransport`では、初期時刻、輸送関数、およびランダム変数を渡す必要があります。ランダム変数は、アウトオブプレースまたはインプレースのいずれかです。実現が`Number`のサブタイプである場合はアウトオブプレースと見なされ、`AbstractArray`のサブタイプである場合はインプレースと見なされます。ここで、ランダム変数は、ランダム数生成器を受け入れる任意の関数であり、アウトオブプレースの場合（例：`rand(rng)`）、またはランダム数生成器と変異させる実現を受け入れる場合（例：`rand!(rng, rv)`）です。

オプションの実現`rv`を指定することができます。実現`rv`は、最初に`AbstractRODEProblem`が解かれるときに使用されます。同じ問題のその後の実行では、`reseed`がfalseに設定されていない限り、ランダム変数`RV`から異なる実現が引き出されます。しかし、`NoiseProblem`の場合、最初の実行ですでに新しい実現が発生し、この場合、`rv`はランダムベクトルの場合に必要な実現プロトタイプと見なすことができます。

最初の例として、ガウスノイズ`W(t) = sin(Yt)`を実装しましょう。ここで、`Y`は正規ランダム変数です。

```julia
f(u, p, t, rv) = sin(rv * t)
t0 = 0.0
W = NoiseTransport(t0, f, randn)
```

ランダムベクトルからスカラーランダムプロセスを構築したい場合は、次のようにランダムベクトルのインプレースバージョンが必要です。輸送関数にパラメータを使用することもでき、その場合は`noise_prototype`を指定する必要があります。

```julia
using Random: randn!
f(u, p, t, rv) = sin(p[1] * t + rv[1]) + cos(p[2] * t + rv[2])
t0 = 0.0
rv = randn(2)
p = (π, 2π)
W = NoiseTransport(t0, f, randn!, rv, noise_prototype = f(nothing, p, t0, rv))
```

ランダムプロセスが多次元であることが期待される場合は、インプレース輸送関数を使用することが望ましく、この場合、`noise_prototype`を指定する必要があります。以下は、`Distributions.jl`からのベータ分布を持つスカラーランダムベクトルの例です。

```julia
f!(out, u, p, t, rv) = (out .= sin.(rv * t))
t0 = 0.0
RV(rng) = rand(rng, Beta(2, 3))
rv = 0.0
W = NoiseTransport(t0, f!, RV, rv, noise_prototype = zeros(4))
```

多次元プロセスを持つランダムベクトルも持つことができ、この場合、`RV`のインプレースバージョンが必要です。例えば。

```julia
using Random: randn!

function f!(out, u, p, t, v)
    out[1] = sin(v[1] * t)
    out[2] = sin(t + v[2])
    out[3] = cos(t) * v[1] + sin(t) * v[2]
    nothing
end

t0 = 0.0
RV!(rng, v) = (v[1] = randn(rng); v[2] = rand(rng))
rv = zeros(2)

W = NoiseTransport(t0, f!, RV!, rv, noise_prototype = zeros(3))
```

`NoiseTransport`はSDEやRODEの駆動ノイズとして使用できます。楽しんでください！
