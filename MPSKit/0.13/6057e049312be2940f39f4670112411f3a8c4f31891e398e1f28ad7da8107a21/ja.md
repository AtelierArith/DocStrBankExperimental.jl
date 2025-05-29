```
transfer_spectrum(above::InfiniteMPS; below=above, tol=Defaults.tol, num_vals=20,
                       sector=first(sectors(oneunit(left_virtualspace(above, 1)))))
```

与えられた `above` 状態と `below` 状態の重なりに対応する左混合転送行列の部分スペクトルを計算します。`sector` キーワード引数を使用して、転送行列の固有ベクトルに対して非自明な全電荷を指定できます。具体的には、各固有ベクトルの定義域に補助空間 `ℂ[typeof(sector)](sector => 1)'` が追加されます。`tol` および `num_vals` キーワード引数は `KrylovKit.eigolve` に渡されます。
