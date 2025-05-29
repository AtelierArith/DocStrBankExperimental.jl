```
add_exch(sim::MicroSim, A::NumberOrTupleOrArrayOrFunction; name="exch")
```

システムに交換エネルギーを追加します。交換エネルギーは次のように定義されます。

$$
  E_\mathrm{ex} = \int_{V} A (\nabla \mathbf{m})^2 \mathrm{d}V
$$

# 例:

```julia
    add_exch(sim, 1e-11)
```

または 

```julia
    add_exch(sim, (2e-12,5e-12,0))
```

または

```julia
    function spatial_A(i,j,k,dx,dy,dz)
        if i<10
            return 1e-11
        else
            return 2e-11
        end
    end
    add_exch(sim, spatial_A)
```
