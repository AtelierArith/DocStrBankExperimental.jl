```
SecondaryLimbDark(primary::AbstractLimbDark,
                  secondary::AbstractLimbDark; 
                  brightness_ratio=1)
SecondaryLimbDark(u_p::AbstractVector, u_s=u_p; kwargs...)
```

二つのリムダークニング法則を組み合わせて、二次食を追加します。係数のベクトルが提供されると、法則は自動的に[`PolynomialLimbDark`](@ref)を使用して構築されます。表面輝度比はホストに対して与えられます。例えば、伴星がホストの半分の明るさであれば、比率は0.5になります。

!!! note "インターフェース"
    [`SecondaryLimbDark`](@ref)は軌道と共にのみ機能します。これは、伴星の基準系を計算する必要があるためです。つまり、`ld(b, r)`のようにインパクトパラメータを使用して直接呼び出すことはできません。


# 数学的形式

$$
f(t, r) = \frac{2f_p(t, r) + \eta r^2 f_s(t', r')}{1 + f_p(t, r) + \eta r^2 f_s(t', r')}
$$

ここで、$f_p$は主フラックス、$f_s$は副フラックス、$\eta$は表面輝度比です。$t'$と$r'$は伴星の基準系からの時間と半径の比に対応します。

# 例

```jldoctest second
using Orbits
# 同じサイズとリムダークニング
r = 1.0
u = [0.4, 0.26]
# 伴星は1/10の明るさ
brightness_ratio = 0.1
ld = SecondaryLimbDark(u; brightness_ratio)
orbit = SimpleOrbit(period=2, duration=0.5)
fp = ld(orbit, 0, r) # 主の出入り
fs = ld(orbit, 1, r) # 副の出入り

fp ≈ brightness_ratio * fs

# 出力
true
```
