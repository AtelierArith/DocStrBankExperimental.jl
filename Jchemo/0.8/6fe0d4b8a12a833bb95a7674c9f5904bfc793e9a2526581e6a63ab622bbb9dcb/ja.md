```
recod_numbyint(x, q)
```

連続変数を整数に再コーディングします。

  * `x` : 置き換える連続変数 (n)。
  * `q` : `x` のクラスを分ける数値。最初のクラスは 1 にラベル付けされます。

例を参照してください。

## 例

```julia
using Jchemo, Statistics
x = [collect(1:10); 8.1 ; 3.1] 

q = [3; 8]
zx = recod_numbyint(x, q)  
[x zx]
probs = [.33; .66]
q = quantile(x, probs) 
zx = recod_numbyint(x, q)  
[x zx]
```
