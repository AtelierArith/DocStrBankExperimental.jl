```
gpu(x)
```

`x`をCUDAデバイスに移動します。これは`Functors.fmap`を使用して、構造体`x`のフィールドを再帰的にトラバースし、`<:AbstractArrays`を`CuArrays`に変換し、isbitsarraysを無視します。カスタム構造体（例：`<:BlochSimulator`または`<:AbstractTrajectory`）の場合、`typeof(x)`を`Functors.@functor`にする必要があります（例：`@functor FISP`）。
