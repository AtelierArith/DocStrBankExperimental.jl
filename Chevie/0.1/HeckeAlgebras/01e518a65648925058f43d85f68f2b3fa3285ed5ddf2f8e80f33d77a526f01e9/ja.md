`char_values(H::HeckeAlgebra,v::Vector{<:Integer})`

Iwahori-Hecke代数の場合、これは`H`の`Tbasis(H)(v)`上のキャラクタ値を計算します。

`H`が複素反射群`W`のHecke代数である場合、このルーチンは`gens(W)`の単語`v`によって定義された`W`の要素のリフト上のキャラクタ値を計算します。

複素反射群に対して、`W`の一般的なHecke代数のキャラクタ表は計算されています（3つの例外を除いて完全ではありません、`representation`を参照）。これは、`s₁,…,sₙ`が`W`のBroué-Malle-Rouquier-Bessis-Michel生成子のリフトである編組群の生成子である場合、`W`の各共役類に少なくとも1つの要素`v`が存在し、それに対する生成子の表現があり、編組群へのリフトのHecke代数における像`Tᵥ`のキャラクタ値が知られていることを意味します。生成子におけるそのような表現は*既知*の単語と呼ばれます（既知の単語のリストは`word.(conjugacy_classes(W))`によって得られます）。単語`v`が既知であれば、計算はキャラクタ表を使用して迅速に行われます。そうでない場合、関数は各不可約表現における`Tᵥ`のトレースを計算します。返される値は、欠落した表現に対して`missing`です（`representation`を参照）。

```julia-repl
julia> W=crg(4)
G₄

julia> H=hecke(W,Pol(:q))
hecke(G₄,q)

julia> char_values(H,[2,1,2])
7-element Vector{Pol{Cyc{Int64}}}:
 q³
 1
 1
 0
 0
 0
 -q
```
