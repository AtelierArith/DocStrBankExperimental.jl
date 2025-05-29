```
periodogram(s::AbstractMatrix; nfft=nextfastfft(size(s)), fs=1, radialsum=false, radialavg=false)
```

2次元信号の周期グラムをFFTによって計算し、Periodogram2オブジェクトを返します。

デフォルトでは2次元の周期グラムが返されます。`radialsum`または`radialavg`がtrueの場合、放射状に合計または平均された周期グラムがPeriodogramオブジェクトとして返されます。

`nfft`はフーリエ変換に使用するポイントの数を指定します。`size(s)` < `nfft`の場合、入力はゼロでパディングされます。デフォルトでは、`nfft`はフーリエ変換が最大の効率で計算できる最も近いサイズです。`fs`は元の信号のサンプルレートで、両方向に適用されます。

`radialsum=true`の場合、`power[k]`の値は$\frac{1}{N}\sum_{k\leq |k'|<k+1} |X[k']|^2$に比例します。`radialavg=true`の場合、これは$\frac{1}{N \#\{k\leq |k'|<k+1\}} \sum_{k\leq |k'|<k+1} |X[k']|^2$に比例します。`|k'|`の計算は、波ベクトルの座標を適切にスケーリングすることによって、非正方形信号を考慮に入れます。 ```
