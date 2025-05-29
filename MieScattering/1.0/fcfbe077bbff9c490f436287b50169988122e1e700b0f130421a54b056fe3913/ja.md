Mie散乱計算は、miepythonに基づいて完璧な球体のためのものです。詳細なドキュメントは(https://miepython.readthedocs.io)にあります。

`MieScattering.jl`は、非吸収、部分吸収、または完全導体の球体による平面波の光散乱を計算するためのJuliaパッケージです。

複素屈折率m、直径d、および波長λを持つ球体の消失効率、散乱効率、後方散乱、および散乱非対称性は次のように求めることができます：

```
    qext, qsca, qback, g = ez_mie(m, d, λ0)
```

角度µ=cos(θ)に対する正規化された散乱値は次の通りです：

```
    Ipar, Iper = ez_intensities(m, d, λ0, µ)
```

サイズパラメータが知られている場合は、次を使用します：

```
    mie(m, x)
```

Mie散乱振幅S1およびS2（複素数）：

```
    mie_S1_S2(m, x, μ)
```

角度µ=cos(θ)に対する正規化されたMie散乱強度：

```
    i_per(m, x, µ)
    i_par(m, x, µ)
    i_unpolarized(m, x, µ)
```
