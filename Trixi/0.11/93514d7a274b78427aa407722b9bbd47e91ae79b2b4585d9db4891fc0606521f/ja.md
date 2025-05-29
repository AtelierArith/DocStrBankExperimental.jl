```
boundary_condition_slip_wall(u_inner, orientation_or_normal, x, t, surface_flux_function,
                              equations::ShallowWaterEquations1D)
```

境界状態を作成するには、法線速度成分を反射し、接線速度成分は変更しないでおきます。境界の水位は内部の値から取られます。

詳細については、書籍の第9.2.5節を参照してください：

  * Eleuterio F. Toro (2001) Shock-Capturing Methods for Free-Surface Shallow Flows 1st edition ISBN 0471987662
