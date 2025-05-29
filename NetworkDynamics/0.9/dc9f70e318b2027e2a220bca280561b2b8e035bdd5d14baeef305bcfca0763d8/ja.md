```
StateMask(i::AbstractArray)
StateMaks(i::Number)
```

`StateMask`は、事前定義された出力関数です。内部状態から選択することによって、コンポーネントモデルの出力を定義するために使用できます。

すなわち、頂点関数内で`g=StateMask(2:3)`は内部状態2と3を出力します。多くの文脈では、`StateMask`はインデックスを提供するだけで暗黙的に構築できます。例えば、`g=1:2`のように。

[`EdgeModel`](@ref)の場合、これは[`Directed`](@ref)、[`Symmetric`](@ref)、[`AntiSymmetric`](@ref)または[`Fiducial`](@ref)結合と組み合わせる必要があります。例えば、`g=Fiducial(1:2, 3:4)`は状態1:2をdstに、状態3:4をsrcに転送します。
