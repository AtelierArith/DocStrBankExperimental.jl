```
d2c(sys::AbstractStateSpace{<:Discrete}, method::Symbol = :zoh; w_prewarp=0)
```

離散時間システムを連続時間システムに変換します。これは、離散時間システムが`method`を使用して離散化されたと仮定します。利用可能なメソッドは`:zoh, :fwdeuler´です。

  * `w_prewarp`: タスティン法を使用する際のプリワープ周波数であり、他のメソッドには影響しません。

詳細は[`d2c_exact`](@ref)を参照してください。
