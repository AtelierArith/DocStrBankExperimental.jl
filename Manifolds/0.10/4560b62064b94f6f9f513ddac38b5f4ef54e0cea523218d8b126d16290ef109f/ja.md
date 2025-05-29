```
log(M::Rotations, p, q)
```

[`Rotations`](@ref) 多様体 `M` 上の対数写像を計算します。これは次のように与えられます。

$$
\log_p q = \operatorname{log}(p^{\mathrm{T}}q)
$$

ここで、$\operatorname{Log}$ は行列の対数を示します。数値的安定性のために、結果は反対称行列の集合に射影されます。

対極回転の場合、この関数は `q` を指す接ベクトルのうちの一つを決定論的に返します。
