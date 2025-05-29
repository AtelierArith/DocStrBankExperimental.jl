```
StepsizeState{P,T} <: AbstractManoptSolverState
```

ラインサーチ内で使用される点と降下方向を格納するための状態であり、これらがメインソルバーの反復と探索方向と異なる場合に使用されます。

# フィールド

  * `p::P`: マニフォールド上の点
  * `X::T`: `p` における接ベクトル。

# コンストラクタ

```
StepsizeState(p,X)
```

# 参照

[`interior_point_Newton`](@ref)
