```
MatsubaraSampling(basis; positive_only=false,
                  sampling_points=default_matsubara_sampling_points(basis; positive_only),
                  factorize=true)
```

`MatsubaraSampling`オブジェクトを構築します。指定されていない場合、`sampling_points`はMatsubaraにおける最高次基底関数の（離散的な）極値として選択されます。これは、このサイズに関して条件付けに対してほぼ最適であることが判明しています（数パーセント以内）。

`positive_only=true`を設定することで、フィッティングされる関数がMatsubara周波数において対称であると仮定します。すなわち：

$$
    Ĝ(iν) = conj(Ĝ(-iν))
$$

または同等に、虚時間において純粋に実であると仮定します。この場合、非負の周波数のみに対して疎なサンプリングが行われ、必要なサンプリング空間の半分がカットされます。`factorize`はSVD分解が計算されるかどうかを制御します。
