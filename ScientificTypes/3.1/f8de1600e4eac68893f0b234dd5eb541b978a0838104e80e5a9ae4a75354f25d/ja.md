```
scitype(X)
```

`X`の科学的タイプ（解釈）は、そのマシンタイプとは異なります。原子的な科学的タイプ（`Continuous`、`Multiclass`など）は、主にパッケージScientificTypesBase.jlで定義された抽象タイプです。科学的タイプは通常、インスタンスを持ちません。

### 例

```
julia> scitype(3.14)
Continuous

julia> scitype([1, 2, missing])
AbstractVector{Union{Missing, Count}}

julia> scitype((5, "beige"))
Tuple{Count, Textual}

julia> using CategoricalArrays

julia> table = (gender = categorical(['M', 'M', 'F', 'M', 'F']),
     ndevices = [1, 3, 2, 3, 2])

julia> scitype(table)
Table{Union{AbstractVector{Count}, AbstractVector{Multiclass{2}}}}

```

テーブルの列の科学的タイプは[`schema`](@ref)を使って調べることもできます。

`scitype`の動作は、[ScientificTypesのドキュメント](https://juliaai.github.io/ScientificTypes.jl/dev/#Summary-of-the-default-convention)で詳しく説明されています。デフォルトの動作の主な特徴は次のとおりです。

  * `AbstractFloat`のscitypeは`Continuous <: Infinite`です。
  * すべての`Integer`のscitypeは`Count <: Infinite`です。
  * すべての`CategoricalValue` `x`のscitypeは、`isordered(x)`の値に応じて`Multiclass <: Finite`または`OrderedFactor <: Finite`です。
  * `String`と`Char`はscitype `Multiclass`または`OrderedFactor`を持ちません。代わりにそれぞれ`Textual`と`Unknown`のscitypeを持ちます。
  * `nothing`と`missing`の科学的タイプは、それぞれ`Nothing`と`Missing`であり、Juliaのタイプでも科学的と見なされます。

!!! note
    サードパーティのパッケージは`scitype`の動作を拡張することがあります。以前は`Unknown`のscitypeを持っていたオブジェクトは、もはやそうでない場合があります。


他にも[`coerce`](@ref)、[`autotype`](@ref)、[`schema`](@ref)を参照してください。
