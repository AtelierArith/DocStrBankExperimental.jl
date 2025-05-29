```
interpolate(r1::TimeRecord, r2::TimeRecord, t::Real; order=0)
```

2つの時間記録（r1、r2）から、ゼロオーダーホールド（order=0）または飽和線形（order=1）を使用して、点tで補間します。
