```
limiter = TrajectoryLimiter(Ts, ẋM, ẍM)
```

次のように呼び出すことができるトラジェクトリリミッタを作成します。

```julia
rlim = limiter(state, r::Number)
# または
X, Ẋ, Ẍ = limiter(state, R::Vector)
# または 
X, Ẋ, Ẍ = limiter(R::Vector) # ゼロ初期状態を使用
```
