```
evolve_operator(evo_gen, time)
```

`time`×`evo_gen`の指数を返します。この関数は、複数の初期状態と固定の`evo_gen`および`time`の場合に便利で、指数を一度計算して異なる初期状態で進化させるのに使用する方が速くなります。

*注意:* パラメータ`evo_gen`は`Matrix`型でなければなりません。`SparseMatrixCSC`型の場合は異なる数値アプローチが使用されます。パッケージ`Expokit`の関数`epmv`を参照してください。

# 例

```jldoctest; setup = :(using QSWalk)
julia> H, L = [0 1; 1 0], [[0 1; 0 0], [0 0; 1 0]]
([0 1; 1 0], Array{Int64,2}[[0 1; 0 0], [0 0; 1 0]])

julia> evolve_operator(evolve_generator(H, L), 4.0)
4×4 Array{Complex{Float64},2}:
 0.499815+0.0im                0.0+0.00127256im  …  0.500185+0.0im
      0.0+0.00127256im  0.00960957+0.0im                 0.0-0.00127256im
      0.0-0.00127256im  0.00870607+0.0im                 0.0+0.00127256im
 0.500185+0.0im                0.0-0.00127256im     0.499815+0.0im
```
