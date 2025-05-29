```
simulate!(εs::AbstractArray, r::VectorAutoregression, Y0=nothing; kwargs...)
```

[`VARProcess`](@ref)を、`r`の係数推定値を使用して、`εs`に指定されたショックと初期値`Y0`を用いてシミュレートします。結果は`εs`をインプレースで上書きすることで保存されます。`Y0`が`nothing`であるか、十分なラグを含まない場合は、ゼロが使用されます。詳細は[`simulate`](@ref)および[`impulse!`](@ref)を参照してください。

# キーワード

  * `nlag::Integer=arorder(var)`: シミュレーションに使用される`var`からのラグの数。
