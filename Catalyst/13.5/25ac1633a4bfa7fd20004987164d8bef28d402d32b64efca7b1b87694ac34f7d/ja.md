```
@reaction
```

単一の [`Reaction`](@ref) オブジェクトを生成します。

例:

```julia
rx = @reaction k*v, A + B --> C + D

# は次のように等価です
@parameters k v
@variables t
@species A(t) B(t) C(t) D(t)
rx == Reaction(k*v, [A,B], [C,D])
```

ここで `k` と `v` はパラメータになり、`A`、`B`、`C`、`D` は変数になります。既存のパラメータ/変数の補間も機能します。

```julia
@parameters k b
@variables t
@species A(t)
ex = k*A^2 + t
rx = @reaction b*$ex*$A, $A --> C
```

注意:

  * 補間されていない速度式に現れる任意の記号はパラメータとして扱われます。反応部分（`α*A + B --> C + D`）では、係数はパラメータとして扱われ、右端の記号は種として扱われます（例: `A,B,C,D`）。
  * [`@reaction_network`](@ref) によってサポートされる任意の *単一* 矢印タイプで機能します。
  * マクロへのJulia変数の補間は、`@reaction_network` マクロと似たように機能します。詳細については [The Reaction DSL](@ref dsl_description) チュートリアルを参照してください。
