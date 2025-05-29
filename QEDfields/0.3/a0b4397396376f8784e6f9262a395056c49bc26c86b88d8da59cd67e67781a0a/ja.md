```
amplitude(field::AbstractPulsedPlaneWaveField, pol::AbstractDefinitePolarization, phi)
```

与えられた偏光方向と位相変数 `phi` の振幅の値を返します。

!!! note "慣習"
    サポートされている方向は2つあります：

    ```Julia
    pol::PolX # -> return envelope(phi)*cos(phi)
    pol::PolY # -> return envelope(phi)*sin(phi)
    ```


!!! note "安全な実装"
    この関数では、ドメインチェックが行われます。すなわち、`phi` がフィールドのドメイン内にある場合、振幅の値が返され、それ以外の場合はゼロが返されます。

