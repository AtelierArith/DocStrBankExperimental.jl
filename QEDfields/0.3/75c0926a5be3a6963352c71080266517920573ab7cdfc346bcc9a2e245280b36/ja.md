```
oscillator(pol::AbstractPolarizaion, phi::Real)
```

与えられた偏光 `pol` に対して、与えられた点 `phi` での基底オシレーターの値を返します。

!!! note "慣例"
    現在のデフォルト実装は次の通りです。

    ```Julia
    PolX() -> cos(phi)
    PolY() -> sin(phi)
    AllPol() -> (cos(phi), sin(phi))
    ```

