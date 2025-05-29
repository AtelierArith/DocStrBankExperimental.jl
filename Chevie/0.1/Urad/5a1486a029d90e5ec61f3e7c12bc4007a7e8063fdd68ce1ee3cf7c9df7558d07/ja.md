このモジュールには、冪零群の要素を用いて計算するための関数が含まれています。具体的には、連結代数的冪零群のボレル部分群の冪零根基に属する要素を計算するためのものです。これらの関数は、オリビエ・デュダスによってGAP3で最初に書かれ、ジャン・ミシェルの古いCコードに部分的に触発されています。

ボレル部分群の冪零根基は、正の根に関連する根部分群の任意の順序での積です。私たちは順序を固定し、要素を表示し比較するための標準形を与えます。

計算は、根部分群間のスタインバーグ関係を使用します。これは、リー代数のシェバレ基の選択から来ています。私たちが従う参考文献は[Carter1972, chapters 4 to 6](biblio.htm#Car72b)ですが、別のシェバレ基の選択を使用することも可能です。`UnipotentGroup`のドキュメントを参照してください。

私たちは、ウィール群`W`によって指定された根データから始め、対応する冪零群の最大冪零部分群に関する情報を含む`struct UnipotentGroup`を構築します。これは、正の根によって決定されるボレル部分群の冪零根基です。

```julia-repl
julia> W=coxgroup(:E,6)
E₆

julia> U=UnipotentGroup(W)
UnipotentGroup(E₆)
```

今、もし`α=roots(W,2)`であれば、根部分群`u_α`の要素`u_α(4)`を構築します：

```julia-repl
julia> U(2=>4)
u2(4)
```

係数を指定しない場合、デフォルトで`u_α(1)`を作成するため、次のようにもなります：

```julia-repl
julia> U(2)^4
u2(4)
```

より複雑な要素を作成することもできます：

```julia-repl
julia> U(2=>4)*U(4=>5)
u2(4)u4(5)

julia> U(2=>4,4=>5)
u2(4)u4(5)
```

根が順序通りでない場合、要素は正規化されます：

```julia-repl
julia> U(4=>5,2=>4)
u2(4)u4(5)u8(-20)
```

根の分解をインデックスの代わりに単純な根で表示することも可能です：

```julia-rep1
julia> xdisplay(U(4=>5,2=>4);root=true)
u₀₁₀₀₀₀(4)u₀₀₀₁₀₀(5)u₀₁₀₁₀₀(-20)
```

根部分群の係数は任意の環の要素であることができます。以下は`Mvp`を使用した例です：

```julia-repl
julia> W=coxgroup(:E,8);U=UnipotentGroup(W)
UnipotentGroup(E₈)

julia> u=U(map(i->i=>Z(2)*Mvp(Symbol("x",Char(i+0x2080))),1:8)...)
u1(x₁)u2(x₂)u3(x₃)u4(x₄)u5(x₅)u6(x₆)u7(x₇)u8(x₈)
```

```julia-rep1
julia> cut(xrepr(u^16;limit=true,root=true),before="u",width=60)
u₂₂₃₄₃₂₁₀(x₁²x₂²x₃³x₄⁴x₅³x₆²x₇)
u₁₂₃₄₃₂₁₁(x₁x₂²x₃³x₄⁴x₅³x₆²x₇x₈)
u₁₂₂₄₃₂₂₁(x₁x₂²x₃²x₄⁴x₅³x₆²x₇²x₈)
u₁₂₂₃₃₃₂₁(x₁x₂²x₃²x₄³x₅³x₆³x₇²x₈)
u₂₂₃₄₃₂₁₁(x₁²x₂²x₃³x₄⁴x₅³x₆²x₇x₈)
u₁₂₂₄₃₃₂₁(x₁x₂²x₃²x₄⁴x₅³x₆³x₇²x₈)
u₁₂₂₄₄₃₂₁(x₁x₂²x₃²x₄⁴x₅⁴x₆³x₇²x₈)
u₂₂₃₄₃₃₂₁(x₁²x₂²x₃³x₄⁴x₅³x₆³x₇²x₈)
u₁₂₃₄₄₃₂₁(x₁x₂²x₃³x₄⁴x₅⁴x₆³x₇²x₈)
u₂₂₃₄₄₃₂₁(x₁²x₂²x₃³x₄⁴x₅⁴x₆³x₇²x₈)
u₂₃₃₅₄₃₂₁(x₁²x₂³x₃³x₄⁵x₅⁴x₆³x₇²x₈)
u₂₂₄₅₄₃₂₁(x₁²x₂²x₃⁴x₄⁵x₅⁴x₆³x₇²x₈)
u₂₃₄₆₅₄₃₂(x₁²x₂³x₃⁴x₄⁶x₅⁵x₆⁴x₇³x₈²)
```

```julia-repl
julia> u^32
()
```

上記の計算は、特性2において`E₈`の冪零群の指数が32であることを示しています。より正確には、二乗することで関与する根の高さが倍増するため、上記の`u¹⁶`は高さ16以上の根のみを含みます。

冪零要素に対してはさまざまな作用が定義されています。ウィール群の要素は（特定の代表を通じて）作用しますが、根部分群がその逆数集合に含まれない限りです：

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> U=UnipotentGroup(W);@Mvp x,y

julia> u=U(1=>x,3=>y)
u1(x)u3(y)

julia> u^W(2,1)
u4(y)u5(x)
```

```julia-repl
julia> u^W(1)
ERROR: u1(x)u3(y) should have no coefficient on root 1
```

半単純要素は共役作用を行います：

```julia-repl
julia> s=SemisimpleElement(W,[E(3),2])
SemisimpleElement{Cyc{Int64}}: <ζ₃,2>

julia> u^s
u1(ζ₃x)u3(2ζ₃y)
```

冪零要素に対しても同様です：

```julia-repl
julia> u^U(2)
u1(x)u3(x+y)u4(-x-2y)u5(x+3y)u6(x²+3xy+3y²)
```
