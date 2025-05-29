```
loop_scaling(M0::Matrix, tol = 0.0001)
```

最適な対角スケーリング行列 `D` を見つけます。これにより `D\M0*D` の条件数が最小化されます。これは正方行列 `M0` のみ適用可能です。オプション `dynamic=true` を使用した [`structured_singular_value`](@ref) も参照してください。ループ伝達関数にスケーリングを見つけて適用するには [`loop_scale`](@ref) を使用してください。
