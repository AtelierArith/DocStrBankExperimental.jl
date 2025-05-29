```
rebuild_lat_internals!(sciml_struct)
```

LatticeReactionSystemをシミュレーションするための内部関数を再構築します。問題や積分器のパラメータ値が更新された場合、この関数を呼び出して更新を考慮する必要があります。ODEシミュレーションの場合、`rebuild_lat_internals!`は次の場合にのみ呼び出す必要があります。

  * エッジパラメータが更新されたとき。
  * 空間的に均一な値を持つパラメータが空間的に不均一な値を与えられたとき（またはその逆）。

引数：

  * `sciml_struct`: 再構築したい問題（例：`ODEProblem`）または積分器。

注意：

  * 現在、`DiscreteProblem`、`JumpProblem`、またはそれらの積分器には対応していません。
  * この関数はパフォーマンスを考慮して作られていないため、パフォーマンスが重要なアプリケーションで何度も呼び出すことは避けてください。

例：

```julia
# 初期の`ODEProblem`を作成
rs = @reaction_network begin
    (k1,k2), X1 <--> X2
end
tr = @transport_reaction D X1
grid = CartesianGrid((2,2))
lrs = LatticeReactionSystem(rs, [tr], grid)

u0 = [:X1 => 2, :X2 => [5 6; 7 8]]
tspan = (0.0, 10.0)
ps = [:k1 => 1.5, :k2 => [1.0 1.5; 2.0 3.5], :D => 0.1]

oprob = ODEProblem(lrs, u0, tspan, ps)

# パラメータ値を更新。
oprob.ps[:ks] = [2.0 2.5; 3.0 4.5]
oprob.ps[:D] = 0.05

# 変更を反映させるために`ODEProblem`を再構築。
rebuild_lat_internals!(oprob)
```
