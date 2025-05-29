```
MomentumReadjustment(tol::AbstractFloat, verbose::Bool)
```

理想的には、dHdu = 0 が曲線の進化全体にわたって成り立ちます。ここで、Hはハミルトニアン/運動量、uはパラメータ空間における曲線の速度です。数値誤差が積分され、これを妨げます。この構造体は、`abs(dHdu) > tol` のときに運動量を再調整し、`dHdu = 0` を回復します。
