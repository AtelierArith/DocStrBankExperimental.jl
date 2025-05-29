```
gali(tands::TangentDynamicalSystem, T; threshold = 1e-12, Δt = 1)
```

`gali(ds::DynamicalSystem, ...)`によって呼び出される低レベルのメソッドです。このメソッドを使用して、異なる初期条件やパラメータをループ処理するために、`tands`に対して[`reinit!`](@ref)を呼び出します。

計算される$\text{GALI}_k$の順序は、`tands`内の偏差ベクトルの数です。

また、`tands`を作成する際に渡す手動でコーディングされたヤコビアンがある場合にも、このメソッドを使用してください。
