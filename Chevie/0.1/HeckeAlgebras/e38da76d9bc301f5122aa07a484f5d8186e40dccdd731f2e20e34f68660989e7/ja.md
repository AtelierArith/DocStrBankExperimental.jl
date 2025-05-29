`hecke( W [, parameter];rootpara=nothing)`

Hecke代数は、複素反射群またはコクセター群`W`のためのものです。`parameter`が指定されていない場合、`1`が仮定され、これは`W`の群代数を与えます。

`parameter`には次の形式が受け入れられます：`parameter`がベクトルまたはタプルでない場合、`fill(parameter,ngens(W))`というベクトルに置き換えられます。もしそれが1つのエントリを持つベクトルであれば、`fill(parameter[1],ngens(W))`に置き換えられます。`parameter`が複数のエントリを持つベクトルである場合、長さは`ngens(W)`でなければならず、各エントリは`W`の対応する生成子のパラメータを表し、同じ`W`-軌道の生成子に対応するエントリは同一である必要があります。最後に、`parameter`が`Tuple`である場合、そのタプルは`W`のハイパープレーン軌道の数と同じ数のエントリを持ち、各エントリは対応するブレイド反射の共役類のパラメータを表します。

`parameter`のエントリは、順序`e`の反射のために、単一のスカラー値または長さ`e`の`Vector`のいずれかであることができます。もしそれが`Vector`であれば、反射のためのパラメータのリスト`[u₀,…,u_(e-1)]`として解釈されます。もしベクトルでない場合、`q`をその値とし、スぺシャル代数のパラメータのリスト`[q,ζ_e,…,ζ_{e-1}]`を指定するものとして解釈されます（したがって、コクセター群の1パラメータ代数のリスト`[q,-1]`）。

Hecke代数を印刷する際、パラメータリストは同じ規則を使用して省略されます。

Hecke代数のキャラクターや表現を計算するには、時々パラメータの根を抽出する必要があります。これらの根は自動的に抽出されます（可能な場合）。コクセター群の場合、キーワード引数`rootpara`を指定することで明示的な根を与えることができます：それがベクトルである場合、`i`番目の位置には`-parameter[i][1]*parameter[i][2]`の平方根が含まれている必要があります；スカラーである場合、`fill(rootpara,ngens(W))`に置き換えられます。

# 例

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> @Pol q
Pol{Int64}: q

julia> H=hecke(W,q)
hecke(B₂,q)

julia> H.para
2-element Vector{Vector{Pol{Int64}}}:
 [q, -1]
 [q, -1]

julia> H=hecke(W,q^2,rootpara=-q)
hecke(B₂,q²,rootpara=-q)

julia> H=hecke(W,q^2)
hecke(B₂,q²)

julia> rootpara(H)
2-element Vector{Pol{Int64}}:
 q
 q

julia> H
hecke(B₂,q²,rootpara=q)

julia> H=hecke(W,[q^2,q^4],rootpara=[q,q^2])
hecke(B₂,Pol{Int64}[q², q⁴],rootpara=Pol{Int64}[q, q²])

julia> H.para,rootpara(H)
(Vector{Pol{Int64}}[[q², -1], [q⁴, -1]], Pol{Int64}[q, q²])

julia> H=hecke(W,9,rootpara=3)
hecke(B₂,9,rootpara=3)

julia> H.para,rootpara(H)
([[9, -1], [9, -1]], [3, 3])

julia> @Mvp x,y,z,t

julia> H=hecke(W,[[x,y]])
hecke(B₂,Vector{Mvp{Int64, Int64}}[[x, y]])

julia> rootpara(H);H
hecke(B₂,Vector{Mvp{Int64, Int64}}[[x, y]],rootpara=ζ₄x½y½)

julia> H=hecke(W,[[x,y],[z,t]])
hecke(B₂,Vector{Mvp{Int64, Int64}}[[x, y], [z, t]])

julia> rootpara(H);H
hecke(B₂,Vector{Mvp{Int64, Int64}}[[x, y], [z, t]],rootpara=Mvp{Cyc{Int64}, Rational{Int64}}[ζ₄x½y½, ζ₄t½z½])

julia> hecke(coxgroup(:F,4),(q,q^2)).para
4-element Vector{Vector{Pol{Int64}}}:
 [q, -1]
 [q, -1]
 [q², -1]
 [q², -1]

julia> hecke(complex_reflection_group(3,1,2),q).para # スペシャルパラメータ
2-element Vector{Vector{Pol{Cyc{Int64}}}}:
 [q, ζ₃, ζ₃²]
 [q, -1]
```
