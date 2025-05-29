'SolomonAlgebra(W,K)'

`(W,S)` を有限コクセター群とします。`w` が `W` の要素であるとき、`R(w)={s ∈ S | l(ws) > l(w)}` と定義します。`I` が `S` の部分集合であるとき、`Y_I={w ∈ W | R(w)=I}`、`X_I={w ∈ W | R(w) ⊃ I}` と定義します。

`X_I` は `W/W_I` の最小長さの左コセット代表の集合であることに注意してください。さて、`y_I=∑_{w ∈ Y_I} w`、`x_I=∑_{w ∈ X_I} w` とします。

これらは `W` の群代数 `ℤ W` の要素です。さて、$Σ(W) = ⊕_{I ⊂ S} ℤ y_I = ⊕_{I ⊂ S} ℤ x_I$ と定義します。これは `ℤW` の部分 `ℤ`-モジュールです。実際、ソロモンはこれが `ℤW` の部分代数であることを証明しました。さて、`K(W)` を `W` のグロタンディーク環とし、`θ:Σ(W)→ K(W)` を `θ(x_I) = Ind_{W_I}^W 1` によって定義された写像とします。ソロモンはこれが代数の同型写像であることを証明しました。これを *ソロモン同型写像* と呼びます。

これは有限コクセター群 `(W,S)` のソロモン降下代数を `K` 上に返します。もし `S=[s₁,…,sᵣ]` であれば、部分集合 `I=[s₁,s₂,s₄]` に対応する要素 `x_I` は |X(124)| として表示されます。`'A:=SolomonAlgebra(W,K)'` は以下のフィールドを持っています：

'A.W': 群 `W`

'A.basis': 基底 `(x_I)_{I ⊂ S}`。

'A.xbasis': 部分集合 `I`（数として書かれる：例えば `[s_1,s_2,s_4]` の場合は `124`）を `x_I` に送る関数。

'A.ybasis': 部分集合 `I` を `y_I` に送る関数。

'A.injection': `A` の `W` の群代数への注入で、'SolomonAlgebraOps.injection(A)' を呼び出すことで得られます。

`'SolomonAlgebra(W,K)'` は `W` にフィールド `W.solomon` を付与し、これは以下のフィールドを含むレコードです：

'W.solomon_subsets': `S` の部分集合の集合

'W.solomon*conjugacy': `W` の放物型部分群の共役類（共役類は、`W.solomon.subsets` の中で部分集合 `I` の位置のリストによって表されます。`W*I` がこの共役類に含まれる場合）。

'W.solomon_mackey': 基本的に有理数上のソロモン代数の構造定数です。

```julia-repl
julia> W=coxgroup(:B,4)
B₄

julia> A=SolomonAlgebra(W)
SolomonAlgebra(B₄,Int64)

julia> X=A.xbasis; X(1,2,3)*X(2,4)
2X₂+2X₄

julia> W.solomon_subsets
16-element Vector{Vector{Int64}}:
 [1, 2, 3, 4]
 [1, 2, 3]
 [1, 2, 4]
 [1, 3, 4]
 [2, 3, 4]
 [1, 2]
 [1, 3]
 [1, 4]
 [2, 3]
 [2, 4]
 [3, 4]
 [1]
 [2]
 [3]
 [4]
 []

julia> W.solomon_conjugacy
12-element Vector{Vector{Int64}}:
 [1]
 [2]
 [3]
 [4]
 [5]
 [6]
 [7, 8]
 [9, 11]
 [10]
 [12]
 [13, 14, 15]
 [16]

julia> Algebras.injection(A)(X(1,2,3))
e_+e₄+e₃₄+e₂₃₄+e₁₂₃₄+e₂₁₂₃₄+e₃₂₁₂₃₄+e₄₃₂₁₂₃₄
```
