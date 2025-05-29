```
gir_lrtran(sys; ltran = false, rtran = false, finite = true, infinite = true, contr = true, obs = true, 
         noseig = false, fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = nϵ) -> (sysr, Q, Z)
```

これは、左および右の変換行列 `Q = [Q1 Q2]` と `Z = [Z1 Z2]` を追加で決定するための関数 `gir` の特別なバージョンです。これにより、結果の記述子システム `sysr = (Ar-λEr,Br,Cr,Dr)` の行列 `Ar`, `Er`, `Br` および `Cr` はそれぞれ `Ar = Q1'*A*Z1`, `Er = Q1'*E*Z1`, `Br = Q1'*B`, `Cr = C*Z1` によって与えられます。ここで、`Q1` と `Z1` の列数は行列 `Ar` の次数と等しくなります。`noseig = false` の場合、`Q` と `Z` は直交します。`ltran = false` の場合は `Q = nothing` となり、`rtran = false` の場合は `Z = nothing` となります。キーワードパラメータの残りの詳細については [`gir`](@ref) を参照してください。
