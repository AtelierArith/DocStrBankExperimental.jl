```
sim!(plant::SimModel, N::Int, u=plant.uop.+1, d=plant.dop; x_0=plant.xop) -> res
```

`plant`のオープンループシミュレーションを`N`タイムステップ実行し、すべての入力に対してデフォルトでユニットバンプテストを行います。

操作された入力$\mathbf{u}$と測定された外乱$\mathbf{d}$は、それぞれ`u`および`d`の値で一定に保たれます。プラントの初期状態$\mathbf{x}(0)$は、`x_0`キーワード引数によって指定されます。この関数は、[`SimResult`](@ref)インスタンスを返し、それらに対して`plot`を呼び出すことで視覚化できます。このメソッドは`plant`の内部状態を変更することに注意してください。

# 例

```jldoctest
julia> plant = NonLinModel((x,u,d,_)->0.1x+u+d, (x,_,_)->2x, 5, 1, 1, 1, 1, solver=nothing);

julia> res = sim!(plant, 15, [0], [0], x_0=[1])
NonLinModelのシミュレーション結果（15タイムステップ）。
```
