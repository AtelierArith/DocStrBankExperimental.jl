`spets(W::ComplexReflectionGroup, F::Matrix=I(rank(W)))`

この関数は、`CoxeterCoset` または `Spets` を返します。`F` は可逆行列であり、次元 `rank(W)` のベクトル空間 `V` の自己同型を表します。有限コクセター群の場合、これは `parent(W)` のルート系の自己同型を誘導しますが、より一般的な複素反射群の場合は単に `W` を安定化します。

返される構造体には特に以下のフィールドがあります：

`.W`: 群 `W`

`.F`: 正のルートを保持する `WF` の一意の要素 `phi` を表す、`V` 上で作用する行列（有限コクセター群の場合）またはより一般的な複素反射群の場合のコセットの「標準的な」代表。

`.phi`: `Perm`、`.F` によって誘導される `W` のルートの置換（一般的な複素反射群の場合、これはスカラーに関して置換である可能性があります）（また、コクセター群の場合、NormalCoset `W .phi` の中で最小の長さの要素）。

最初の例では、有限体 `FF(q)` 上の一般ユニタリ群 `GU_3(q)` に対応するコクセターコセットを作成します。

```julia-repl
julia> W=rootdatum(:gl,3)
gl₃

julia> gu3=spets(W,-reflrep(W,W()))
²A₂Φ₂

julia> F4=coxgroup(:F,4);D4=reflection_subgroup(F4,[1,2,16,48])
F₄₍₁‚₂‚₉‚₁₆₎=D₄₍₃₂₁₄₎

julia> spets(D4,[1 0 0 0;0 1 2 0;0 0 0 1;0 0 -1 -1])
F₄₍₉‚₁₆‚₁‚₂₎=³D₄₍₃₄₁₂₎
```

`spets(W::ComplexReflectionGroup,p::Perm)`

このバージョンでは、`F` はそれが行う単純なルートの置換によって定義されます。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> spets(W,Perm(1,3))
²A₃
```
