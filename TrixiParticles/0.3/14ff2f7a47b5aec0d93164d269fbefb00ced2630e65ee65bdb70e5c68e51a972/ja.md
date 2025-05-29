```
SourceTermDamping(; damping_coefficient)
```

ダンピングステップが必要な場合に使用されるソース項です。項 $-c \cdot v_a$ は、粒子 $a$ の加速度 $\frac{\mathrm{d}v_a}{\mathrm{d}t}$ に追加され、ここで $c$ はダンピング係数、$v_a$ は粒子 $a$ の速度です。

# キーワード

  * `damping_coefficient`:    上記の係数 $d$。係数が高いほど、より多くのダンピングが行われます。静止した流体をダンピングするための良い出発点は、係数 `1e-4` です。

# 例

```jldoctest; output = false
source_terms = SourceTermDamping(; damping_coefficient=1e-4)

# output
SourceTermDamping{Float64}(0.0001)
```
