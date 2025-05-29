`position_regular_class(WF,ζ::Root1=1)`

`WF` を反射群または反射コセットとし、`ζ` をその中のある要素が非自明な `ζ`-固有空間を持つような単位根とします。この関数は、`WF` の共役類のインデックスを返します。その `ζ`-固有空間は、`W` の要素のすべての `ζ`-固有空間の中で最大です。もし `WF` の要素が非自明な `ζ`-固有空間を持たない場合、この関数は `nothing` を返します。

固有値 `ζ` は、整数 `d` を指定することによっても指定できます（この場合、`ζ=E(d)` を指定します）または、分数 `a//b` を指定することによっても指定できます（この場合、`ζ=E(b,a)` を指定します）。省略した場合、`ζ` は `1` と見なされます。

```julia-repl
julia> W=coxgroup(:E,8)
E₈

julia> position_regular_class(W,30)
65

julia> W=complex_reflection_group(6)
G₆

julia> L=twistings(W,[2])[4]
G₆₍₂₎=G₃‚₁‚₁[ζ₄]Φ′₄

julia> position_regular_class(L,7//12)
2
```
