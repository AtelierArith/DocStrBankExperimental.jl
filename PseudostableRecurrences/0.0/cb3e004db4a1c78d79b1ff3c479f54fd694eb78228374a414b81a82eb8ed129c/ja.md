```
BandedSylvesterRecurrencePlan{FA<:Function, FB<:Function, FC<:Function, INIT<:Function} <: AbstractLinearRecurrencePlan
```

参照してください [`BandedSylvesterRecurrence`](@ref)。

# プロパティ

  * `fA::FA, fB::FB, fC::FC`: `BandedSylvesterRecurrence` のために `A`、`B`、および `C` を生成する関数。関数は `f(eltype, size...)` の形式である必要があります。
  * `init::INIT`: 再帰を開始するために $X$ の最初の数列を生成する関数。関数は `f(eltype, size...)` の形式である必要があります。
  * `size::Dims{2}`: $X$ のサイズ。
  * `bandB::NTuple{2,Int}`: `B` のバンド幅。`B` は無限の上バンド幅を持つことができますが、それはストンシルが無限の幅を持つことを引き起こし、実際には `B` の上バンド幅は常に $X$ の有限の幅によって制限されます。
  * `firstind::Int`: 計算される最初の列。デフォルト値は `bandB[2]+1` です。
