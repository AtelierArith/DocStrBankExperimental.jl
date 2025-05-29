```
MTE_SMT(
    axon::Stick = Stick()
    extra::Zeppelin = Zeppelin()
    fracs::Float64 = 0.5
    )
```

これは、低b値のin vivoイメージングのためのマルチTE球面平均技術を使用したモデルです。コンパートメントのT2が考慮されています。このモデルに関する特定の参考文献はまだありませんが、このトピックに関連する以前の研究を参照できます：

Kaden, E., Kruggel, F., Alexander, D.C., 2016. 脳の白質における軸索ごとの拡散係数の定量的マッピング。Magn Reson Med 75, 1752–1763. https://doi.org/10.1002/MRM.25734

Kaden, E., Kelm, N. D., Carson, R. P., Does, M. D., & Alexander, D. C. (2016). マルチコンパートメント顕微拡散イメージング。NeuroImage, 139, 346-359.

Veraart, J., Novikov, D.S., Fieremans, E., 2017. TE依存の拡散イメージング（TEdDI）は、コンパートメントのT2緩和時間を区別します。https://doi.org/10.1016/j.neuroimage.2017.09.030

Gong, T., Tong, Q., He, H., Sun, Y., Zhong, J., Zhang, H., 2020. MTE-NODDI: コンパートメント特異的T2緩和時間から非T2重み付け信号分率を解きほぐすためのマルチTE NODDI。Neuroimage 217. https://doi.org/10.1016/j.neuroimage.2020.116906
