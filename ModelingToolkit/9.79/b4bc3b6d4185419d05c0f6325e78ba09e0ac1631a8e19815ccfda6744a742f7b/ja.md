```julia
NonlinearSystem(
    sys::ModelingToolkit.AbstractODESystem
) -> Any

```

`ODESystem`を`NonlinearSystem`に変換し、その定常状態（導関数がゼロである状態）を解きます。任意の微分変数`D(x) ~ f(...)`は`0 ~ f(...)`に変換されます。返されるシステムは簡略化されません。入力システムが`complete`であれば、返されるシステムもそうなります。
