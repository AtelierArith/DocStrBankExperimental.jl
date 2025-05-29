```
powder_average(f, cryst, radii, n; seed=0)
```

構造因子の強度に対して粉末平均を計算します。`radii`は逆長さの単位を持ち、逆空間における球状シェルを定義します。[フィボナッチ格子](https://arxiv.org/abs/1607.04590)は、球上に`n`点をほぼ均一に配置します。異なるシェル上のサンプル点は、ランダムな回転を通じて非相関化されます。一貫した乱数`seed`は再現可能な結果をもたらします。関数`f`はq点のリストを受け入れ、[`intensities`](@ref)または[`intensities_static`](@ref)を呼び出す必要があります。

# 例

```julia
radii = range(0.0, 3.0, 200)
res = powder_average(cryst, radii, 500) do qs
    intensities(swt, qs; energies, kernel)
end
plot_intensities(res)
```
