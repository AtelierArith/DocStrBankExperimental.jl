```
DeterministicIteratedMap <: DiscreteTimeDynamicalSystem
DeterministicIteratedMap(f, u0, p = nothing; t0 = 0)
```

反復マップによって定義された決定論的離散時間動的システムは次のようになります：

$$
\vec{u}_{n+1} = \vec{f}(\vec{u}_n, p, n)
$$

`DeterministicIteratedMap`の別名は`DiscreteDynamicalSystem`です。

パラメータコンテナ`p`と初期時間`t0`をオプションで設定します。

`f, u0`に関する構築手順については、DynamicalSystems.jlのチュートリアルを参照してください。
