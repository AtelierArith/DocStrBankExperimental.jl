```julia
NoiseProcess{T, N, Tt, T2, T3, ZType, F, F2, inplace, S1, S2, RSWM, C, RNGType} <:
{T, N, Vector{T2}, inplace}
```

`NoiseProcess`は次のように定義された型です：

```julia
NoiseProcess(t0, W0, Z0, dist, bridge;
    iip = SciMLBase.isinplace(dist, 3),
    rswm = RSWM(), save_everystep = true,
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true, reseed = true)
```

  * `t0` は最初の時間点です。
  * `W0` はプロセスの最初の値です。
  * `Z0` は擬似プロセスの最初の値です。これは高次のアルゴリズムに必要です。必要ない場合は `nothing` に設定します。
  * `dist` は時間に対するステップの分布です。
  * `bridge` はブリッジ分布です。オプションですが、適応性と新しい値での補間には必要です。
  * `covariance` はノイズプロセスの共分散行列です。提供されない場合、ノイズは各変数で無相関であると仮定されます。
  * `save_everystep` はブラウン運動の時系列のすべてのステップを保存するかどうかです。
  * `rng` は乱数を生成するために使用されるローカルRNGです。
  * `reset` は各解決時にプロセスをリセットするかどうかです。
  * `reseed` は各解決時にプロセスを再シードするかどうかです。

`dist` のシグネチャは次の通りです：

```julia
dist!(rand_vec, W, dt, rng)
```

インプレース関数の場合、そして

```julia
rand_vec = dist(W, dt, rng)
```

それ以外の場合。`bridge` のシグネチャは次の通りです：

```julia
bridge!(rand_vec, W, W0, Wh, q, h, rng)
```

そして、アウトオブプレースの構文は次の通りです：

```julia
rand_vec = bridge!(W, W0, Wh, q, h, rng)
```

ここで、`W` はノイズプロセス、`W0` は現在の区間の左側、`Wh` は現在の区間の右側、`h` は区間の長さ、`q` は補間が行われている左側の割合です。

## 直接構築の例

`NoiseProcess` を直接構築する最も簡単な方法は、例を通じて示すことです。ここでは、ガウスホワイトノイズを生成する `NoiseProcess` を直接構築する方法を示します。

これは `randn!` を使用するノイズプロセスです。複素数用に `(randn()+im*randn())/sqrt(2)` のための特別なディスパッチが追加されています。この関数は `DiffEqNoiseProcess.wiener_randn`（または `!` を付けたもの）です。

最初に定義する必要があるのはノイズ分布です。これは、$W(x)$ が $x∈[t₀,t]$ の場合に $W(t+dt)$ を生成する方法です。ガウスホワイトノイズの場合、次のことがわかっています。

$$
W(dt) ∼ N(0,dt)
$$

$$
W(0)=0
$$

の場合、これがステッピング分布を定義します。したがって、そのノイズ分布関数は次の通りです：

```julia
@inline function WHITE_NOISE_DIST(W, dt, rng)
    if W.dW isa AbstractArray && !(W.dW isa SArray)
        return @fastmath sqrt(abs(dt)) * wiener_randn(rng, W.dW)
    else
        return @fastmath sqrt(abs(dt)) * wiener_randn(rng, typeof(W.dW))
    end
end
```

アウトオブプレースバージョンの場合、インプレースバージョンの場合は次の通りです：

```julia
function INPLACE_WHITE_NOISE_DIST(rand_vec, W, dt, rng)
    wiener_randn!(rng, rand_vec)
    sqrtabsdt = @fastmath sqrt(abs(dt))
    @. rand_vec *= sqrtabsdt
end
```

オプションで、ブリッジ分布を提供することができます。これは、$W(qh)$ の分布であり、$q∈[0,1]$ の場合に $W(0)=0$ および $W(h)=Wₕ$ がわかっているときです。ブラウン運動の場合、これはブラウンブリッジとして知られており、次の分布を持つことが知られています：

$$
W(qh) ∼ N(qWₕ,(1-q)qh)
$$

したがって、アウトオブプレースとインプレースのバージョンは次の通りです：

```julia
function WHITE_NOISE_BRIDGE(W, W0, Wh, q, h, rng)
    if W.dW isa AbstractArray
        return @fastmath sqrt((1 - q) * q * abs(h)) * wiener_randn(rng, W.dW) + q * Wh
    else
        return @fastmath sqrt((1 - q) * q * abs(h)) * wiener_randn(rng, typeof(W.dW)) +
                         q * Wh
    end
end
function INPLACE_WHITE_NOISE_BRIDGE(rand_vec, W, W0, Wh, q, h, rng)
    wiener_randn!(rng, rand_vec)
    #rand_vec .= sqrt((1.-q).*q.*abs(h)).*rand_vec.+q.*Wh
    sqrtcoeff = @fastmath sqrt((1 - q) * q * abs(h))
    @. rand_vec = sqrtcoeff * rand_vec + q * Wh
end
```

これらの関数は次のようにノイズプロセスに配置されます：

```julia
NoiseProcess(t0, W0, Z0, WHITE_NOISE_DIST, WHITE_NOISE_BRIDGE; kwargs)
NoiseProcess(t0, W0, Z0, INPLACE_WHITE_NOISE_DIST, INPLACE_WHITE_NOISE_BRIDGE; kwargs)
```

オプションで、タイムステッピングの拒否のための代替適応アルゴリズムを提供できます。`RSWM()` はデフォルトでメモリ付き拒否サンプリング3アルゴリズム（RSwM3）です。

標準のコンストラクタは単に次の通りです：

```julia
function WienerProcess(t0, W0, Z0 = nothing)
    NoiseProcess(t0, W0, Z0, WHITE_NOISE_DIST, WHITE_NOISE_BRIDGE; kwargs)
end
function WienerProcess!(t0, W0, Z0 = nothing)
    NoiseProcess(t0, W0, Z0, INPLACE_WHITE_NOISE_DIST, INPLACE_WHITE_NOISE_BRIDGE; kwargs)
end
```

これにより、ウィーナープロセスが生成され、`step!(W,dt)` でステップを進め、`W(t)` として補間できます。
