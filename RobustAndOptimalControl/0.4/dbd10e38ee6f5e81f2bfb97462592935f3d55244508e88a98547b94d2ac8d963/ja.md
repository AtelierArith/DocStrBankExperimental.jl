```
bilineard2c(Ad::AbstractArray, Bd::AbstractArray, Cd::AbstractArray, Dd::AbstractArray, Ts::Number; tolerance=1e-12)
```

状態空間におけるバランスの取れた双線形変換。このメソッドは、離散時間システムの連続時間同等物を計算します。すなわち、

```
G_c(z) = z2s[G_d(z)]
```

以下のことを達成する方法で (i) 変換において無限大のL-無限大ノルムを保持する (ii) ||B||*2=||C||*2 という意味でBとCをバランスさせるシステムを見つける (iii) あるマップs2z[]に対してG*d(z) = s2z[z2s[G*d(z)]]を満たす
