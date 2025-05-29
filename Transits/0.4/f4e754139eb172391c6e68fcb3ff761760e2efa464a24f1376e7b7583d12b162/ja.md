```
PolynomialLimbDark(u::AbstractVector)
```

多項式リムダークニングを解析的積分を用いて行います。`u`ベクトルの長さは使用される多項式の次数に相当します。例えば、`[0.2, 0.3]`は二次リムダークニングに対応します。

# 数学的形式

$$
I(\mu) \propto 1 - u_1(1-\mu) - u_2(1-\mu)^2 - \dots - u_N(1-\mu)^N
$$

これは次の級数に相当します。

$$
I(\mu) \propto -\sum_{i=0}^N{u_i(1-\mu)^i}
$$

ここで、$u_0 \equiv -1$と定義します。

# 例

```jldoctest poly
u = [0.4, 0.26] # 二次およびそれ以下は100%解析的
ld = PolynomialLimbDark(u)
ld(0.1, 0.01)

# 出力
0.9998787880717668
```

```jldoctest poly
u2 = vcat(u, ones(12) ./ 12)
ld2 = PolynomialLimbDark(u2)
ld2(0.1, 0.01)

# 出力
0.9998740059086433
```

# 参考文献

> [Agol, Luger, Foreman-Mackey (2020)](https://ui.adsabs.harvard.edu/abs/2020AJ....159..123A)
>
> "多項式リムダークニングを持つ星のための解析的惑星トランジット光曲線と導関数"


> [Luger et al. (2019)](https://ui.adsabs.harvard.edu/abs/2019AJ....157...64L)
>
> "starry: 解析的隠蔽光曲線"

