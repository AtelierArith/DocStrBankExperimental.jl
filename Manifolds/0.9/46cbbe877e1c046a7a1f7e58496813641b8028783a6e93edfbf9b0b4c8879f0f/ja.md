```
log(M::Rotations, p, X)
log(M::OrthogonalMatrices, p, X)
log(M::UnitaryMatrices, p, X)
```

対数写像を計算します。すなわち、結果の $X$ はリー代数で表されます。

```
log_p q = \log(p^{\mathrm{H}q)
```

これは数値的安定性のために斜対称行列に射影されます。
