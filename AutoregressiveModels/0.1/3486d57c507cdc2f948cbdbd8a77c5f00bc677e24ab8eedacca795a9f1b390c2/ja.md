```
simulate!(εs::AbstractArray, var::VARProcess, Y0=nothing; kwargs...)
```

`εs`に指定されたショックと初期値`Y0`を使用して`var`プロセスをシミュレートします。結果は`εs`をインプレースで上書きすることで保存されます。`Y0`が`nothing`であるか、十分なラグを含まない場合は、ゼロが使用されます。詳細は[`simulate`](@ref)および[`impulse!`](@ref)を参照してください。

# キーワード

  * `nlag::Integer=arorder(var)`: シミュレーションに使用される`var`からのラグの数。
