# 代数群と半単純要素

代数的閉体 `K` を固定し、`𝐆` を `K` 上の連結可解代数群とします。`𝐓` を `𝐆` の最大トーラスとし、`X(𝐓)` を `𝐓` のキャラクター群（または `Y(𝐓)` を `𝐓` の1次元部分群の双対格子）とし、`Φ`（または `Φ^`）を `𝐓` に関する `𝐆` の根（またはコルート）とします。

このとき、`𝐆` は *根データ* `(X(𝐓),Φ, Y(𝐓),Φ^)` によって同型類を決定されます。代数的な用語で言えば、これは次元が `𝐓` の *階数*（または `𝐆` の *階数* とも呼ばれる）である自由な `ℤ`-格子 `X=X(𝐓)` を与え、根系 `Φ ⊂ X` を与え、同様に双対根 `Φ^⊂ Y=Y(𝐓)` を与えることを含みます。

これは、コクセター群 `W` のための我々の設定のわずかな一般化によって得られます。今回は、`W` が作用するベクトル空間 `V` の標準基底が `X` の `ℤ`-基底であると仮定し、`Φ` はこの `X` の基底で表現された単純根を行として持つ行列 `simpleroots(W)` によって指定されます。同様に、`Φ^` は選ばれた `X` の基底に対して双対の基底である `Y` の単純コルートを行として持つ行列 `simplecoroots(W)` によって記述されます。`X` と `Y` の間の双対ペアリングは標準的なものであり、すなわちベクトル `x∈ X` と `y∈ Y` の間のペアリングは `transpose(x)*y` によって与えられます。したがって、`simplecoroots(W)*permutedims(simpleroots(W))=cartan(W)` という関係が成り立たなければなりません。

これは、上記で説明した2つの行列 `simpleroots(W)` と `simplecoroots(W)` を引数に持つ関数 `rootdatum` を使用することによって得られます。根は `V` を生成する必要はないので、行列は正方行列である必要はありません。例えば、階数3の線形群の根データは次のように得られます：

```julia-repl
julia> W=rootdatum([-1 1 0;0 -1 1],[-1 1 0;0 -1 1])
A₂Φ₁

julia> reflrep(W,W(1))
3×3 Matrix{Int64}:
 0  1  0
 1  0  0
 0  0  1
```

ここで、ウィール群は3文字の対称群であり、`X` の基底の置換によって作用します。`X` の次元 `size(simpleroots(W),2)` は *階数* であり、根によって生成される部分空間の次元 `size(simpleroots(W),1)` は *半単純階数* と呼ばれます。この例では、階数は3であり、半単純階数は2です。

デフォルトの形 `W=coxgroup(:A,2)` は、隣接代数群（中心が自明な同型類の群）を定義します。この場合、`Φ` は `X` の基底であるため、`simpleroots(W)` は単位行列であり、`simplecoroots(W)` は根系のカータン行列 `cartan(W)` です。

形 `coxgroup(:A,2,sc=true)` は、半単純単連結代数群を構築します。この場合、`simpleroots(W)` は `cartan(W)` の転置であり、`simplecoroots(W)` は単位行列です。

根データの極端な形は、より便利に指定できます：`W` が自明な `coxgroup()` である場合（この場合 `𝐆` はトーラスです）、根データには根がなく、したがって階数 `r` によって完全に決定されます。関数 `torus(r)` はそのような根データを構築します（これは `rootdatum` に2つの `0×r` 行列を与えることによっても得られます）。

最後に、`rootdatum` 関数は、適切な `simpleroots(W)` と `simplecoroots(W)` 行列を与えることによって得られる結果を与える代数群のいくつかの馴染みのある名前も理解します：

```julia-repl
julia> rootdatum(:gl,3)   # 前の例と同じ
gl₃
```

理解される根データの型は `:gl, :pgl, :sl, :slmod, :tgl :sp, :csp, :psp, :so, :pso, :cso, :halfspin, :gpin, :spin, :E6, :E6sc, :CE6, :E7, :E7sc, :CE7, :E8, :F4, :G2` です。

## 半単純要素

半単純要素を2つの方法で構築します。最初の方法は、代数的閉体 `K` 上の `𝐓` の有限順の要素に対してであり、これは `Y⊗ ℚ /ℤ` の要素と1対1対応しており、その分母は `K` の特性に対して素です。これらは、`0≤r<1` となる `Rational` のベクトル `r` として表されます。関数 `ss` は、そのような有理数のベクトルから半単純要素を構築します。

より一般的には、体 `K` 上のトーラス `𝐓` は `(Kˣ)^n` に同型であり、ここで `n` は `𝐓` の次元です。したがって、`Kˣ` の要素のベクトルは、関数 `SemisimpleElement` によって生成されるより一般的な表現です。この設定では、`ss` の結果は自然に `Vector{Root1}` として解釈されるため、そのようなベクトルを持つ `SemisimpleElement` を呼び出すことによっても得られます。

```julia-repl
julia> G=rootdatum(:sl,4)
sl₄

julia> ss(G,[1//3,1//4,3//4,2//3])
SemisimpleElement{Root1}: <ζ₃,ζ₄,ζ₄³,ζ₃²>

julia> SemisimpleElement(G,[E(3),E(4),E(4,3),E(3,2)])
SemisimpleElement{Root1}: <ζ₃,ζ₄,ζ₄³,ζ₃²>

julia> L=reflection_subgroup(G,[1,3])
A₃₍₁₃₎=A₁×A₁Φ₁

julia> C=algebraic_center(L)
(Z0 = SubTorus(A₃₍₁₃₎=A₁×A₁Φ₁,[1 2 1]), AZ = Group(SemisimpleElement{Root1}[<1,1,-1>]), descAZ = [[1, 2]], ZD = Group(SemisimpleElement{Root1}[<-1,1,1>, <1,1,-1>]))

julia> T=torsion_subgroup(C.Z0,3)
Group(SemisimpleElement{Root1}[<ζ₃,ζ₃²,ζ₃>])

julia> e=sort(elements(T))
3-element Vector{SemisimpleElement{Root1}}:
 <1,1,1>
 <ζ₃,ζ₃²,ζ₃>
 <ζ₃²,ζ₃,ζ₃²>
```

上記では、`SL₄` のレヴィ部分群 `L` が `2×2` のブロック対角行列から構成されています。関数 `algebraic_center` は、中心 `Z` の中立成分 `Z⁰` を `Y(Z⁰)` の基底によって表し、`Z⁰` に対するトーラスの補完部分 `S` を同様に `Y(S)` の基底によって表し、`Z` のクラスを `S` 内で選ばれた半単純要素によって表します。クラス `Z/Z⁰` は、フィールド `.descAZ` によって与えられる基本群と1対1対応します。詳細については [`algebraic_center`](@ref) を参照してください。最後に、`Z⁰` 内の階数3の半単純要素が計算されます。

```julia-repl
julia> e[3]^G(2)
SemisimpleElement{Root1}: <ζ₃²,1,ζ₃²>

julia> orbit(G,e[3])
6-element Vector{SemisimpleElement{Root1}}:
 <ζ₃²,ζ₃,ζ₃²>
 <ζ₃²,1,ζ₃²>
 <ζ₃,1,ζ₃²>
 <ζ₃²,1,ζ₃>
 <ζ₃,1,ζ₃>
 <ζ₃,ζ₃²,ζ₃>
```

ここでは、係数が有限体 `FF(4)` にある半単純要素を用いて、上記と同じ計算が行われます。これは `sl₄(𝔽₄)` の要素を表します。

```julia-repl
julia> G=rootdatum(:sl,4)
sl₄

julia> s=SemisimpleElement(G,Z(4).^[1,2,1])
SemisimpleElement{FFE{2}}: <Z₄,Z₄²,Z₄>

julia> s^G(2)
SemisimpleElement{FFE{2}}: <Z₄,1,Z₄>

julia> orbit(G,s)
6-element Vector{SemisimpleElement{FFE{2}}}:
 <Z₄,Z₄²,Z₄>
 <Z₄,1,Z₄>
 <Z₄²,1,Z₄>
 <Z₄,1,Z₄²>
 <Z₄²,1,Z₄²>
 <Z₄²,Z₄,Z₄²>
```

`𝐆` 内の半単純要素の中心化 $C_𝐆 (s)$ を計算できます：

```julia-repl
julia> G=coxgroup(:A,3)
A₃

julia> s=ss(G,[0,1//2,0])
SemisimpleElement{Root1}: <1,-1,1>

julia> centralizer(G,s)
A₃₍₁₃₎=(A₁A₁)Φ₂
```

結果は `ExtendedReflectionGroup` です。反射群部分は $C_𝐆 ⁰(s)$ のウィール群であり、拡張部分は反射部分のダイアグラム自己同型として取られた $C_𝐆 (s)$ の代表です。ここでは、$C_𝐆 ⁰(s)ϕ$ というコセットとして印刷され、$C_𝐆 (s)$ を生成します。
