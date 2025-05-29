```
set_mu_s(sim::AtomisticSim, init::NumberOrArrayOrFunction)
```

与えられた原子システム `sim` のために磁気モーメント `mu_s` を設定します。

### 使用例

システム全体に均一な磁気モーメントを設定するには、次のようにします：

```julia
set_mu_s(sim, 2 * mu_B)
```

または、関数を使用して空間的に変化する磁気モーメントを定義することもできます。たとえば、特定の磁気モーメントを持つ円形領域を設定するには：

```julia
function circular_shape(i, j, k, dx, dy, dz)
    if (i - 50.5)^2 + (j - 50.5)^2 <= 50^2
        return 2 * mu_B
    end
    return 0.0
end
set_mu_s(sim, circular_shape)
```

ここでの `circular_shape` 関数は、半径50（格子単位）の円の中にある原子に `2 * mu_B` を割り当て、外側の領域には `0.0` を設定します。
