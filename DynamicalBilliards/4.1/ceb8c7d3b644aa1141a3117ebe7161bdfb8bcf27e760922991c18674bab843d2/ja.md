```
parallelize(f, bd::Billiard, t, particles; partype = :threads)
```

利用可能な粒子に対して関数 `f` を並列化します。並列化のタイプは `:threads` または `:pmap` で、これは `using DynamicalBilliards` *の前に* `addprocs` で初期化されたスレッドまたはワーカープールを使用します。

`particles` は次のように指定できます：

  * 粒子の `Vector`。
  * 整数 `n` にオプションで角速度 `ω` が続くもの。これは [`randominside`](@ref) を使用します。

ここで使用可能な関数は：

  * [`meancollisiontime`](@ref)
  * [`escapetime`](@ref)
  * [`lyapunovspectrum`](@ref) （最大の指数のみを返します）
  * [`boundarymap`](@ref) （2ベクトルのベクトル *および* `arcintervals` のベクトルを返します）
