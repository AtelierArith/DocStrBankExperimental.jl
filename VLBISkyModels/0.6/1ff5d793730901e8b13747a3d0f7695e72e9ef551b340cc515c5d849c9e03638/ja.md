```
Stretch(α, β)
Stretch(r)
```

モデルをx方向とy方向にストレッチしました。すなわち、新しい強度は Iₛ(x,y) = 1/(αβ) I(x/α, y/β) であり、モデルのフラックスを保持するために強度を再正規化します。

# 例

```julia-repl
julia> modify(Gaussian(), Stretch(2.0)) == stretched(Gaussian(), 2.0, 1.0)
true
```

引数が1つだけ与えられた場合、両方の方向に同じストレッチが適用されると仮定します。

```julia-repl
julia> Stretch(2.0) == Stretch(2.0, 2.0)
true
```
