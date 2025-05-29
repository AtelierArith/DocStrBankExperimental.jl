```
monitor(sol::AbstractODESolution; vars=nothing, tspan=nothing)
```

粒子の軌道やその他の物理量をモニタリングするためのプロットレシピです。

# 引数

  * `sol::AbstractODESolution`: ODEソルバーによって返された解。

# キーワード

  * `vars`: プロットする変数を選択するために使用される引数。デフォルト値は [4, 5, 6] です。
  * `tspan::Tuple`: プロットする時間の範囲。例えば、tspan = (0, 1) のようになります。

## vars

この関数における `vars` の使い方は [`orbit`](@ref) のそれとは異なります。リストでなければならず、その長さは3でなければなりません。要素の型は Integer または Function でなければなりません。関数の形式は `orbit` によって規定されたものと同じです。例えば、

```julia
Eₖ(xu) = mₑ*(xu[4]^2 + xu[5]^2 + xu[6]^2)/2
monitor(sol, vars=[1, 2, Eₖ])
```
