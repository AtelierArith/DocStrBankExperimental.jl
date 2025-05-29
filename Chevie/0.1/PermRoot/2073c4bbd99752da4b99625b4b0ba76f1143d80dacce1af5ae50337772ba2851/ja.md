`reflection_length(W::PermRootGroup,w::Perm)` または `reflength`

この関数は、反射表現における `w` の固有値のうち、1 に等しくないものの数を返します。有限コクセター群において、これは `w` の反射長に等しく、すなわち `w` が積である最小の反射の数です。これは、`w` がコクセター要素の反射長で割り切れる場合、一般的な良生成複素反射群においても成り立ちます。

```julia-repl
julia> W=coxgroup(:A,4)
A₄

julia> reflength(W,longest(W))
2

julia> reflength(W,W(1,2,3,4))
4
```
