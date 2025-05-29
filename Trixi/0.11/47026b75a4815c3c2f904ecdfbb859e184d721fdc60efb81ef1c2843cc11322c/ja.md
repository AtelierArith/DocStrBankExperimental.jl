```
VolumeIntegralPureLGLFiniteVolume(volume_flux_fv)
```

サブセル有限体積スキームの [`VolumeIntegralShockCapturingHG`](@ref) のみを使用する体積積分です。

これは、LGLタイプのサブセルメッシュ（LGL = レジャンドル-ガウス-ロバット）上で形式的にO(1)精度の有限体積スキームを提供します。

!!! warning "実験的な実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


## 参考文献

  * Hennemann, Gassner (2020) "A provably entropy stable subcell shock capturing approach for high order split form DG" [arXiv: 2008.12044](https://arxiv.org/abs/2008.12044)
