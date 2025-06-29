```julia
mutable struct BorderedArray{vectype1, vectype2}
```

これは、2つの配列または配列とスカラーを保持する配列（ただし `<: AbstractArray` ではありません）を定義します。これは、例えば関数に制約（位相など）を追加したい場合に便利です。このパッケージ全体で擬似弧長連続（PALC）、折れ線/ホップ点の連続、周期軌道などに使用されます。また、周期軌道を (軌道, 周期) として定義するためにも使用されます。そのため、`cat`、`vcat` などの便利な代替手段です。私たちは、現在のパッケージを一般的な「配列」に適用したいと考えているため、AbstractArrayのサブタイプにはしないことにしました。詳細は [Requested methods for Custom State](@ref) を参照してください。最後に、`x[end]` の操作が遅くなる可能性があるため、GPUにとっても便利です。
