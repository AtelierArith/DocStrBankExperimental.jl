```
u_modified!(i::DEIntegrator,bool)
```

`bool`を設定し、`u`に変更があったかどうかを示します。これにより、ソルバーは不連続性を処理できます。コールバックが使用されている場合、デフォルトではこれがtrueであると見なされます。これにより、`t+dt`での導関数の再計算が行われますが、アルゴリズムがFSALであり、`u`が区間の終わりで不連続な変化を経験しない場合は必要ありません。したがって、コールバック内で`u`が変更されていない場合、導関数計算への単一の呼び出しは`u_modified!(integrator,false)`によって省略できます。
