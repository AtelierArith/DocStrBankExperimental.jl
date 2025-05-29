```
Xc = plyap(sys::AbstractStateSpace, Ql; kwargs...)
```

リャプノフソルバーで、`Q`の`L`コレスキー因子を取り、`Xc*Xc' = X`となる三角行列`Xc`を返します。
