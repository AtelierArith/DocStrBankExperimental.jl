```
new_od = transform_ODESystem(od::ODESystem, tr::TransformationStructure)

- ODEシステムのパラメータを変換trを介して再パラメータ化します。
- ODE方程式内のパラメータpの任意のインスタンスはtr.inv_p_transform(p)で置き換えられます。
- デフォルトのパラメータ値p0がある場合、それらはtr.p_transform(p0)に変更されます。
```
