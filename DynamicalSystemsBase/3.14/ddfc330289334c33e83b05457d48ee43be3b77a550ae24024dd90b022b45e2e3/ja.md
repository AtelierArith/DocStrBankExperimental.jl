```
StroboscopicMap <: DiscreteTimeDynamicalSystem
StroboscopicMap(ds::CoupledODEs, period::Real) → smap
StroboscopicMap(period::Real, f, u0, p = nothing; kwargs...)
```

与えられた `period` にわたって時間依存（非自律的）[`CoupledODEs`](@ref) システムの反復を正確に生成する離散時間力学系です。2番目のシグネチャは最初に [`CoupledODEs`](@ref) を作成し、その後最初のものを呼び出します。

`StroboscopicMap` は [`DynamicalSystem`](@ref) インターフェースに従います。さらに、システムの周期を新しい値に設定する `set_period!(smap, period)` 関数が提供されており、これはパラメータのように振る舞います。このシステムは離散時間にあるため、[`current_time`](@ref) と [`initial_time`](@ref) は整数です。初期時間は常に 0 であり、`current_time` は経過した周期をカウントします。これらの関数を `StroboscopicMap` の `parent` に対して呼び出すことで、対応する連続時間を取得できます。対照的に、[`reinit!`](@ref) は連続時間での `t0` を期待します。

便利なコンストラクタ

```julia
StroboscopicMap(T::Real, f, u0, p = nothing; diffeq, t0 = 0) → smap
```

も提供されています。

さらに [`PoincareMap`](@ref) も参照してください。
