```
dependents(rx, network)
```

[`Reaction`](@ref) と [`ReactionSystem`](@ref) を与えると、反応速度法則が依存する*非定数*種と変数のベクトルを返します。例えば、

`k*W, 2X + 3Y --> 5Z + W`

の場合、返されるベクトルは `[W(t),X(t),Y(t)]` になります。

注意:

  * アロケートします
  * いかなるサブシステム内の依存関係をチェックしません。
  * 定数種は依存関係とは見なされず、内部的にはパラメータとして扱われます。
  * 反応速度式が依存する非種状態変数があり、それが依存関係に含まれる場合、すなわち

    ```julia
    @parameters k
    @variables t V(t)
    @species A(t) B(t) C(t)
    rx = Reaction(k*V, [A, B], [C])
    @named rs = ReactionSystem([rx], t)
    issetequal(dependents(rx, rs), [A,B,V]) == true
    ```
