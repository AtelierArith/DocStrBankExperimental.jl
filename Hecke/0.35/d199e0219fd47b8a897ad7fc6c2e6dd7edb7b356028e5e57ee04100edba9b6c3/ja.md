```
saturate(A::SMat{ZZRingElem}) -> SMat{ZZRingElem}
```

$$
A
$$

の飽和を計算します。すなわち、$\mathbf{Q}\otimes M \cap \mathbf{Z}^n$の基底を求めます。ここで、$M$は$A$の行スパンであり、$n$は$A$の行数です。

同等に、$TA$が整数であり、$TA$の基本因子がすべて自明であるような可逆有理行列$T$に対して$TA$を返します。
