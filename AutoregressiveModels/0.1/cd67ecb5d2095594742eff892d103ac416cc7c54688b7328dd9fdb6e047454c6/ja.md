```
simulate!(out::AbstractArray, εs::AbstractArray, arma::ARMAProcess, y0=nothing)
```

`arma`プロセスを`εs`で指定されたショックと初期値`y0`を使用してシミュレートします。結果は`out`に格納されます。`y0`が`nothing`であるか、十分なラグを含まない場合は、ゼロが使用されます。詳細は[`simulate`](@ref)および[`impulse!`](@ref)を参照してください。
