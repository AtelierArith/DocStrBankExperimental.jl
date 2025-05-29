```
produce_orbitdiagram(ds::CoupledODEs, P, args...; kwargs...)
```

`CoupledODEs`のための軌道図を生成するショートカット関数です。この関数は、単に`ds`を`P`に基づいて[`PoincareMap`](@ref)または[`StroboscopicMap`](@ref)のいずれかに変換し、次に[`orbitdiagram](@ref)`(map, args...; kwargs...)を呼び出します。

`P`が`Union{Tuple, Vector}`の場合、`P`を`plane`として[`PoincareMap`](@ref)が作成されます。`P`が`Real`の場合、`P`を周期として[`StroboscopicMap`](@ref)が作成されます。

マップを作成することがなぜ有用であるかについては、[^DatserisParlitz2022]の第4章を参照してください。

[^DatserisParlitz2022]: Datseris & Parlitz 2022, *Nonlinear Dynamics: A Concise Introduction Interlaced with Code*, [Springer Nature, Undergrad. Lect. Notes In Physics](https://doi.org/10.1007/978-3-030-91032-7)
