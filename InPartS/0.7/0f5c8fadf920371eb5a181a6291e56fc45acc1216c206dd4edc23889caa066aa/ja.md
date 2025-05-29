```
addparticles!(sim; centerpos::Vector{SVector}, kwargs...)
```

[`addparticle!`](@ref)と同様ですが、複数の粒子用です（その名の通り）。

指定された`centerpos`の数だけ粒子を作成します。ベクトルのkwargsでは、`i`番目のエントリが`i`番目の粒子を構築するために使用されます。他のすべてのkwargsはすべての粒子に使用されます。

## 拡張ヘルプ

### 使用例

```julia
addparticles(sim, centerpos = [SA[0.0, 0.0], SA[1.0, 1.0]], foo = [0.4, -4.5], bar = 5.0, baz = (1.0, 2.0))
```

`[0.0, 0.0]`に1つの粒子を、`foo = 0.4`、`bar = 5.0`、`baz = (1.0, 2.0)`で作成し、`[1.0, 1.0]`にもう1つの粒子を、`foo = -4.5`、`bar = 5.0`、`baz = (1.0, 2.0)`で作成します。
