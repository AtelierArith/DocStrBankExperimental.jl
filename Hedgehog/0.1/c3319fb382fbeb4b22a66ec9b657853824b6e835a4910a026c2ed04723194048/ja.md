```
RectVolSurface(reference_date, rate, spot, tenors, strikes, prices; kwargs...)
```

観測されたオプション価格から `RectVolSurface` をキャリブレーションします。オプションの `call_put_matrix` を処理し、補間/外挿のカスタマイズを可能にします。
