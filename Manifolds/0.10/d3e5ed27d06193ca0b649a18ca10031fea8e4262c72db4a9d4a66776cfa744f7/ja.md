```
log(M::Rotations, p, X)
log(M::OrthogonalMatrices, p, X)
log(M::UnitaryMatrices, p, X)
```

対数写像を計算します。すなわち、結果として得られる $X$ はリー代数で表されるので、

$$
\log_p q = \log(p^{\mathrm{H}}q)
$$

これは数値的安定性のために反対称行列に射影されます。
