```
sysdual = gdual(sys, rev = false) 
sysdual = transpose(sys, rev = false)
```

記述子システム `sys = (A-λE,B,C,D)` の転送関数行列 `G(λ)` に対して、記述子システムの双対システムの実現 `sysdual = (Ad-λEd,Bd,Cd,Dd)` を計算します。ここで、`Ad = transpose(A)`、`Ed = transpose(E)`、`Bd = transpose(C)`、`Cd = transpose(B)`、`Dd = transpose(D)` であり、転送関数行列 `Gdual(λ)` は `sysdual` のもので、`Gdual(λ) = transpose(G(λ))` となります。

`rev = true` の場合、転置は状態変数の逆順序の置換と組み合わされ、次のようになります：`sysdual = (P*Ad*P-λP*Ed*P,P*Bd,Cd*P,Dd)`。ここで、`P` は第二対角線に1がある置換行列です。
