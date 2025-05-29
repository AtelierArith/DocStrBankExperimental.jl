```
discretemeasure(
    support::AbstractVector,
    probs::AbstractVector{<:Real}=FillArrays.Fill(inv(length(support)), length(support)),
)
```

`support` と対応する `probabilities` を持つ有限離散確率測度を構築します。確率ベクトル引数が渡されない場合、サポート内の各エントリに等しい確率が割り当てられます。

# 例

```julia
using KernelFunctions
# 行はサンプルに対応
μ = discretemeasure(RowVecs(rand(7,3)), normalize!(rand(10),1))

# 列はサンプルに対応し、各サンプルは等しい確率を持つ
ν = discretemeasure(ColVecs(rand(3,12)))
```

!!! note
    `support` が1Dベクトルの場合、構築された測度はソートされます。例えば `mu = discretemeasure([3, 1, 2],[0.5, 0.2, 0.3])` の場合、`mu.support` は `[1, 2, 3]` となり、`mu.p` は `[0.2, 0.3, 0.5]` になります。また、`RowVecs(rand(3))` や `[[1],[3],[4]]` のような1D分布を渡すことは避けてください。これは、アルゴリズムがより効率的な単変量ケースではなく、多変量ケースにディスパッチされます。


!!! warning
    この関数、特にその戻り値は安定しておらず、将来のリリースで変更される可能性があります。

