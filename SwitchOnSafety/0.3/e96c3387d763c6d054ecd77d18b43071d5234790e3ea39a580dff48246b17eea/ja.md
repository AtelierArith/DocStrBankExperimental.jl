```
invariant_sets(system::AbstractHybridSystem, optimizer_constructor,
               set_variables::AbstractVector{<:SetProg.AbstractVariable};
               volume_heuristic = nth_root,
               infeasibility_certificates = nothing,
               verbose=1,
               λ=Dict{transitiontype(system), Float64}(),
               enabled = states(system))
```

システムのモードに対して、`optimizer_constructor`によって提供されるソルバーを使用して、`set_variables`のファミリーの最大不変集合を計算します。集合の体積は`volume_heuristic`を使用して推定されます。プログラムが実現不可能な場合、各遷移の証明書は`infeasibility_certificates`に保存されます。非同次の包含については、S手続きがバイリニア行列不等式（BMI）である可能性があり、これは解くのがNP困難です。それを避けるために、辞書`λ`で使用する`λ`の値を提供します。計算においていくつかの状態とそれに関わる遷移を無視するには、それらを含まない`enabled`ベクターを指定してください。
