```
modify_exchange_with_truncated_dipole_dipole!(sys::System, cutoff, μ0_μB²)
```

[`enable_dipole_dipole!`](@ref)と同様に、この関数の目的は、磁気モーメント間の長距離の双極子-双極子相互作用を導入することです。`enable_dipole_dipole!`がエワルド和を使用するのに対し、この関数は指定された`cutoff`距離での切断を伴う実空間ペア結合を使用します。カットオフが比較的小さい場合、この関数は`enable_dipole_dipole!`よりも速い可能性があります。

!!! warning "既存の結合の変更"
    この関数は、双極子-双極子相互作用を追加することによってスピン間の既存の二次結合を変更します。したがって、すべての他のペア結合が指定された*後*に呼び出す必要があります。逆に、`set_exchange!`、`set_pair_coupling!`などの呼び出しは、この関数によって導入された双極子-双極子相互作用を不可逆的に削除します。

