```
bilinearc2d(Ac::AbstractArray, Bc::AbstractArray, Cc::AbstractArray, Dc::AbstractArray, Ts::Number; tolerance=1e-12)
```

状態空間におけるバランスビリニア変換。このメソッドは、次のように連続時間システムの離散時間等価を計算します。

$$
G_d(z) = s2z[G_c(s)]
$$

この方法は以下を達成します (i) 変換において無限大のL-infinityノルムを保持する (ii) $||B||_2=||C||_2$の意味でBとCをバランスさせるシステムを見つける (iii) あるマップz2s[]に対して$G_c(s) = z2s[s2z[G_c(s)]]$を満たす
