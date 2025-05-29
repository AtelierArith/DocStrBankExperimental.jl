```julia
mc2sp(mc, α, fftlen)

```

mc2spはメルケプストラムをパワースペクトルエンベロープに変換します。

$$
c\_{\alpha}(m) -> |X(\omega)|^{2}
$$

同等: `exp(2real(MelGeneralizedCepstrums.mgc2sp(mc, α, 0.0, fftlen)))` `MelGeneralizedCepstrums.mgc2sp`は対数振幅スペクトルを返すことに注意してください。
