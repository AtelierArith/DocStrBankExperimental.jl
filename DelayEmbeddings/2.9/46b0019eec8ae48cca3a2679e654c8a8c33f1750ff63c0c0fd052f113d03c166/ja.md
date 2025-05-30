```
embed(s, d, τ [, h])
```

遅延座標を使用して次元 `d` と遅延時間 `τ` で `s` を埋め込み、結果を [`StateSpaceSet`](@ref) として返します。オプションで重み `h` を使用できます。詳細は以下を参照してください。

ここで `τ > 0` の場合、一般化されたバージョンについては [`genembed`](@ref) を使用してください。

## 説明

`τ` が整数の場合、埋め込まれた空間の $n$ 番目のエントリは次のようになります。

$$
(s(n), s(n+\tau), s(n+2\tau), \dots, s(n+(d-1)\tau))
$$

代わりに `τ` が整数のベクトルであり、`length(τ) == d-1` である場合、$n$ 番目のエントリは次のようになります。

$$
(s(n), s(n+\tau[1]), s(n+\tau[2]), \dots, s(n+\tau[d-1]))
$$

結果として得られるセットは、適切な `d` と `τ` の場合、元のシステムから記録された時系列と同じ不変量（例えば、リャプノフ指数など）を持つことができます。これはタケンズ埋め込み定理として知られています [^Takens1981] [^Sauer1991]。異なる遅延時間のケースは、多くの時間スケールを持つシステムを埋め込むことを可能にします [^Judd1998]。

提供された場合、`h` は埋め込まれた空間のエントリに掛ける重みとなります。`h` が実数の場合、埋め込みは次のようになります。

$$
(s(n), h \cdot s(n+\tau), h^2 \cdot s(n+2\tau), \dots,h^{d-1} \cdot s(n+γ\tau))
$$

そうでない場合、`h` は長さ `d-1` のベクトルであり、各エントリの重みを直接決定します。

## 参考文献

[^Takens1981] : F. Takens, *Detecting Strange Attractors in Turbulence — Dynamical Systems and Turbulence*, Lecture Notes in Mathematics **366**, Springer (1981)

[^Sauer1991] : T. Sauer *et al.*, J. Stat. Phys. **65**, pp 579 (1991)

[^Judd1998]: K. Judd & A. Mees, [Physica D **120**, pp 273 (1998)](https://www.sciencedirect.com/science/article/pii/S0167278997001188)

[^Farmer1988]: Farmer & Sidorowich, [Exploiting Chaos to Predict the Future and Reduce Noise"](http://www.nzdl.org/gsdlmod?e=d-00000-00---off-0cltbibZz-e--00-1----0-10-0---0---0direct-10---4-------0-1l--11-en-50---20-home---00-3-1-00-0--4--0--0-0-11-10-0utfZz-8-00&a=d&cl=CL3.16&d=HASH013b29ffe107dba1e52f1a0c_1245)
