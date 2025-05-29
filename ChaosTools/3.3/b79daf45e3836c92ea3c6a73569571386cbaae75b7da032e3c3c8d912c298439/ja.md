```
lyapunovspectrum(tands::TangentDynamicalSystem, N::Int; Ttr, Δt, show_progress)
```

`lyapunovspectrum(ds::DynamicalSystem, ...)`によって呼び出される低レベルのメソッドです。このメソッドを使用して、異なる初期条件やパラメータをループ処理するために、`tands`に対して[`reinit!`](@ref)を呼び出します。

また、`tands`を作成する際に渡す手動でコーディングされたヤコビアンがある場合にも、このメソッドを使用してください。
