`Cbasis(H::HeckeAlgebra)`

は、Iwahori-Hecke代数 `H` の `C`-基底を与える関数を返します。代数 `H` には `rootpara` 関数が定義されている必要があります。この基底は次のように定義されます（例えば、[(5.1)Lusztig1985](biblio.htm#Lus85)を参照）。`W` を基礎となるコクセター群とします。`x,y ∈ W` の場合、$P_{x,y}$ は対応するカジダン–ルスティグ多項式です。もし $\{T_w ∣ w∈ W\}$ が通常の T-基底を示すなら、$C_x=\sum_{y\le x}(-1)^{l(x)-l(y)}P_{y,x}(q^{-1})q_x^{1/2}q_y^{-1}  T_y$ であり、`x  ∈ W` の場合です。例えば、`s ∈ S` の場合、`Cₛ=qₛ⁻½Tₛ-qₛ½T₁` となります。したがって、`T`-基底と `C`-基底の間の変換行列は下三角単位行列であり、対角線上には `qₛ` の単項式があります。1パラメータの場合（すべての `qₛ` が `v²` に等しい場合）、`C` 基底の乗法則は次のように与えられます：

`Cₛ⋅Cₓ =-(v+v⁻¹)Cₓ`、もし `sx<x` の場合、そして `Cₛₓ+∑ₜ μ(t,x)Cₜ` もし `sx>x` の場合。

ここで、和はすべての `t` にわたっており、`t<x` で、`l(t)` と `l(x)` が異なる奇偶性を持ち、`st<t` であるものです。係数 `μ(t,x)` はカジダン–ルスティグ多項式 $P_{x,t}$ における次数 `(l(x)-l(t)-1)/2` の係数です。

返される関数は、コクセター単語、コクセター群の要素、または Hecke 要素（その後 `C'` 基底に変換される）を表す整数のリスト（ベクトルまたは引数のリストとして）を引数として取ることができます。

```julia-repl
julia> W=coxgroup(:B,3);H=hecke(W,Pol(:v)^2)
hecke(B₃,v²)

julia> T=Tbasis(H);C=Cbasis(H);T(C(1))
-vT.+v⁻¹T₁

julia> C(T(1))
v²C.+vC₁
```

`C`-基底の要素に対するキャラクタ値も次のように計算できます：

```julia-repl
julia> ref=reflrep(H)
3-element Vector{Matrix{Pol{Int64}}}:
 [-1 0 0; -v² v² 0; 0 0 v²]
 [v² -2 0; 0 -1 0; 0 -v² v²]
 [v² 0 0; 0 v² -1; 0 0 -1]
```

```julia-rep1
julia> c=CharTable(H).irr[charinfo(W).extRefl[[2]],:]
1×10 Matrix{Pol{Int64}}:
 3  2v²-1  v⁸-2v⁴  -3v¹²  2v²-1  v⁴  v⁴-2v²  -v⁶  v⁴-v²  0

julia> hcat(char_values.(C.(classreps(W)),Ref(c))...)
1×10 Matrix{Pol{Int64}}:
 3  -v-v⁻¹  0  0  -v-v⁻¹  2  0  0  1  0
```
