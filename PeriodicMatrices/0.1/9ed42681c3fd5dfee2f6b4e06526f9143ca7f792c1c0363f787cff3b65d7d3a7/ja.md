```
 FourierFunctionMatrix(Afun, T) -> A::FourierFunctionMatrix
```

連続時間フーリエ関数行列の表現。

周期 `T` のフーリエ関数行列オブジェクト `A` は、サブ周期 `T′ = T/k` の周期行列 `Afun(t)` のフーリエ級数表現を使用して構築されます。ここで、`Afun(t)` の各エントリは次の形式を持ちます。

```
         p
  a_0 +  ∑ ( ac_i*cos(i*t*2*π/T′)+as_i*sin(i*2*π*t/T′) ) ,
        i=1
```

ここで、`k ≥ 1` はサブ周期の数（デフォルト: `k = 1`）です。フーリエ表現を含む行列 `Afun`、周期 `T`、およびサブ周期の数 `k` は、それぞれ `A.M`、`A.period`、および `A.nperiod` を介してアクセスできます。
