```
function approximate(
    m::Int,
    M::AbstractManifold,
    f::Function; # :: [-1, 1]^m -> M^n
    p=[], # 線形化する周りの点。デフォルトは100サンプルのKarcher平均。
    base_approximate=approximate_vector::Function, # :: (m::Int) -> (n::Int) -> ([-1, 1]^m -> R^n) -> ([-1, 1]^m -> R^n)
    kwargs...
    )::Function # :: [-1, 1]^m -> M^n
```

リーマン正規座標チャートを使用して、マンifold値関数を近似します。
