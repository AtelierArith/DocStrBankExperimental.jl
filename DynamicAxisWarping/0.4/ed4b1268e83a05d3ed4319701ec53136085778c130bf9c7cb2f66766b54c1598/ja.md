```
gdtw(
    x,
    y,
    ::Type{T}  = Float64;
    symmetric::Bool = true,
    M::Int     = 100,
    N::Int     = 100,
    t          = range(T(0), stop = T(1), length = N),
    cache::GDTWWorkspace = GDTWWorkspace(T, M, length(t)),
    λcum       = T(0.01),
    λinst      = T(0.01),
    η          = T(1 / 8),
    max_iters  = 3,
    metric     = (x, y) -> norm(x - y),
    Rcum       = abs2,
    smin::Real = T(0.001),
    smax::Real = T(5.0),
    Rinst      = symmetric  ?
                    ϕ′ -> ( (smin <= ϕ′ <= smax)
                        && (smin <= 2 - ϕ′ <= smax) ) ? (ϕ′-1)^2 : typemax(T)
                            :
                    ϕ′ -> (smin <= ϕ′ <= smax) ? (ϕ′-1)^2 : typemax(T),
    verbose    = false,
    warp       = zeros(T, length(t)),
    callback   = nothing,
) where T -> cost, ϕ, ψ
```

一般的なDTW距離を計算します。[DB19](https://arxiv.org/abs/1905.12893)に従います。

`ϕ(s)`を見つけることを目的としています。

```
∫ metric(x(ϕ(s)), y(ψ(s))) + λinst*Rinst(ϕ'(s) - 1) + λcum*Rcum(ϕ(s) - s) ds
```

区間`s ∈ [0,1]`で、`ψ(s) = 2s - ϕ(s)`（`symmetric=true`の場合）または`ψ(s) = s`（`symmetric = false`の場合）。積分は時間で`N`点に離散化されます（または`t`が指定されている場合は`t`の時間に従います）。さらに、各可能な時間`s`で得られる`ϕ`（およびそれにより`ψ`）の可能な値は`M`点に離散化されます。

`max_iters > 1`の場合、最適な`ϕ`を得るために二重離散化された問題を解いた後、前の最適値の周りの区間で`ϕ(s)`の新しい離散化を選択して問題を再度解決します（その幅はパラメータ`η`によって制御されます）。これは、問題が合計`max_iters`回解決されるまで繰り返されます。`verbose=true`を設定すると、各イテレーションでコストが印刷されます。「十分に高い」`max_iters`の値は、コストが十分に安定する時点を調べることで選択できます。

パラメータは次のとおりです：

  * `x`: ワープする連続時間信号（離散データからそのような信号を生成するには[`LinearInterpolation`](@ref)を参照）
  * `y`: ワープする連続時間信号
  * `T`: 問題で使用される数値型
  * `symmetric`: trueの場合、`ψ(s) = 2s - ϕ(s)`、それ以外の場合は`ψ(s) = s`。
  * `t`: `[0,1]`の時間の離散化；`t`または`N`のいずれかを指定する必要があります
  * `M`: ワーピングパスによって得られる値の離散化
  * `metric`: 時間点で信号間の違いを計算する関数`metric(u,v) -> ℝ`（たとえば、Distances.jlの距離）
  * `Rcum`: 累積ワープに対するペナルティ関数
  * `Rinst`: 瞬時ワーピングに対するペナルティ関数。`[smin, smax]`の外では無限大である必要があります。
  * `smin`, `smax`: 許可される瞬時ワーピングの最小値と最大値。`smin > 0`および`smin < smax`である必要があります。
  * `λcum`, `λinst`: それぞれ`Rcum`および`Rinst`の正則化定数

次のものは、同じ`M`および`N`（または`length(t)`）を持つ距離計算の間で事前に割り当てられ、再利用される可能性があります。

  * `cache`: `GDTW.GDTWWorkspace{T}(N,M)`によって生成された行列とベクトルのキャッシュ
