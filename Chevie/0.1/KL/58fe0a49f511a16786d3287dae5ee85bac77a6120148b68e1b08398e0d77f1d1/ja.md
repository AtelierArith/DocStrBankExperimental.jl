このモジュールはカズダン-ルスティグ多項式と基底を定義し、W-グラフと漸近代数を計算します。

`ℋ` をコクセター系 `(W,S)` のイワホリ-ヘッケ代数とし、二次関係 `(Tₛ-uₛ₀)(Tₛ-uₛ₁)=0` を `s∈ S` に対して持つとします。もし `-uₛ₀uₛ₁` が平方根 `wₛ` を持つなら、基底 `Tₛ` をスケールして新しい基底 `tₛ=-Tₛ/wₛ` を得ることができ、二次関係 `(tₛ-vₛ)(tₛ+vₛ⁻¹)=0` が成り立ちます。ここで `vₛ=wₛ/uₛ₁` とします。カズダン-ルスティグ基底と多項式が定義できる最も一般的な場合は、パラメータ `vₛ` が乗法に関して全順序アーベル群 `Γ` に属する場合です（[Lusztig1983](biblio.htm#Lus83)を参照）。`Γ⁺= {γ∈ Γ∣γ>0}` および `Γ⁻={γ⁻¹∣γ∈ Γ⁺}={γ∈ Γ∣γ<0}` と設定します。

したがって、`ℋ` は環 `ℤ[Γ]` 上で定義され、`Γ` の群代数であり、`ℋ` の二次関係は各 `s∈ S` に対して `vₛ∈ Γ⁺` を関連付け、`(tₛ-vₛ)(tₛ+vₛ⁻¹)=0` となります。また、`qₛ=vₛ²` と設定し、二次関係 `(Tₛ-qₛ)(Tₛ+1)=0` を持つ基底 `Tₛ=vₛtₛ` を定義します。`w∈ W` で簡約表現 `w=s₁…sₙ` を持つとき、$q_w∈ Γ⁺$ を $q_w^½=v_{s₁}…v_{sₙ}$ によって定義し、$q_w=(q_w^½)²$ とします。これにより $T_w=q_w^½t_w$ が得られます。

`ℋ` 上のバー反転を線形性によって定義します：`ℤ[Γ]` 上では $\overline{∑_{γ∈ Γ}a_γγ}= ∑_{γ∈ Γ} a_γ γ⁻¹$ によって定義し、`ℋ` に拡張して $\overline T_s=T_s^{-1}$（同等に $\overline t_s=t_s^{-1}$）とします。次に、カズダン-ルスティグ基底 $C^′_w$ は、バー反転に対して安定であり、$t_w$ に対して $∑_{w∈ W}Γ⁻.t_w$ で合同な唯一の基底として定義されます。

基底 $C^′_w$ は次のように計算できます。`ℤ[Γ]` の要素 $R_{x,y}$ を $T_y⁻¹=∑_x \overline{R_{x,y⁻¹}} q_x⁻¹T_x$ によって定義します。次に、カズダン-ルスティグ多項式（この一般的な文脈では、`ℤ[Γ]` のカズダン-ルスティグ要素と呼ぶべきで、`qₛ` によって生成される `ℤ[Γ]` の部分代数に属します）を帰納的に定義します。$P_{x,w}=τ_{≤(q_w/q_x)^½}  (∑_{x<y≤w}R_{x,y}P_{y,w})$ であり、ここで `τ` は切り捨てを表します：$τ_≤\nu ∑_{γ∈  Γ} a_γγ=  ∑_{γ≤\nu}a_γγ$; 帰納はしたがってブルハット順序に対して減少する `x` で行われ、$P_{w,w}=1$ から始まります。したがって、$C^′_w=∑_y q_w^{-1/2} P_{y,w}T_y$ となります。

カズダン-ルスティグ基底 `C`, `D`, `C'`, `D'` のためのチェビエコードは、1994年頃にアンドリュー・マサスによって最初に書かれ、彼はイワホリ-ヘッケ代数の基底の設計にも貢献し、マーフィ基底などの他の基底も実装しました。私たちのコードはそのコードから進化しました。不均一なパラメータの場合のコードは、1999年頃にF.ディーニュとJ.ミッシェルによって書かれました。カズダン-ルスティグ基底は `C′` 基底から計算されます。

`ℤ[Γ]` がローレンツ多項式環である場合、バー操作は変数の逆数を取ることになり、切り捨ては `ν` の次数以下の項を保持します。任意の群 `Γ` を使用することが可能ですが、`bar`:$∑_{γ∈   Γ}   a_γγ↦  ∑_{γ∈  Γ}  a_γγ⁻¹$, `positive_part`  : $∑_{γ∈  Γ} a_γγ↦  ∑_{γ≥ 1}  a_γγ$ および `negative_part`: $∑_{γ∈  Γ}  a_γγ  ↦  ∑_{γ≤  1}  a_γγ$ が `ℤ[Γ]` 上で定義されている限りです。これらの操作は、カズダン-ルスティグ基底を計算するためにプログラム内部で使用されます。

また、カズダン-ルスティグ左セルを研究する機能も提供します（等パラメータヘッケ代数の場合）。

```julia-repl
julia> W=coxgroup(:H,3)
H₃

julia> c=left_cells(W)
22-element Vector{LeftCell{FiniteCoxeterGroup{Perm{Int16},Cyc{Int64}}}}:
 LeftCell<H₃: duflo= character=φ₁‚₀>
 LeftCell<H₃: duflo=123 character=φ₁‚₁₅>
 LeftCell<H₃: duflo=(15) character=φ₅‚₅>
 LeftCell<H₃: duflo=(10) character=φ₅‚₅>
 LeftCell<H₃: duflo=(14) character=φ₅‚₅>
 LeftCell<H₃: duflo=7 character=φ₅‚₅>
 LeftCell<H₃: duflo=(12) character=φ₅‚₅>
 LeftCell<H₃: duflo=(9,12) character=φ₅‚₂>
 LeftCell<H₃: duflo=(5,11) character=φ₅‚₂>
 LeftCell<H₃: duflo=13 character=φ₅‚₂>
 ⋮
 LeftCell<H₃: duflo=(8,13) character=φ₃‚₆+φ₃‚₈>
 LeftCell<H₃: duflo=(1,15) character=φ₃‚₆+φ₃‚₈>
 LeftCell<H₃: duflo=3 character=φ₃‚₁+φ₃‚₃>
 LeftCell<H₃: duflo=2 character=φ₃‚₁+φ₃‚₃>
 LeftCell<H₃: duflo=1 character=φ₃‚₁+φ₃‚₃>
 LeftCell<H₃: duflo=6 character=φ₄‚₃+φ₄‚₄>
 LeftCell<H₃: duflo=(13) character=φ₄‚₃+φ₄‚₄>
 LeftCell<H₃: duflo=(11) character=φ₄‚₃+φ₄‚₄>
 LeftCell<H₃: duflo=9 character=φ₄‚₃+φ₄‚₄>
```

左セルに対しては、関数 `elements`、[`character`](@ref)、`representation` および [`Wgraph`](@ref) も参照してください。操作 `length`、`in`（`elements` を参照）および `==`（デュフロ反転を比較する）は、左セルに対しても定義されています。`character(c)` が計算された場合、`c.a` もバインドされ、`c` の要素と `character(c)` の不可約成分の共通のルスティグの `a`-関数の値を保持します。

最後に、ベンチマーク

```benchmark
julia> function test_kl(W)
         q=Pol(); H=hecke(W,q^2,rootpara=q)
         C=Cpbasis(H); T=Tbasis(H)
         [T(C(w)) for w in elements(W)]
       end
test_kl (generic function with 1 method)

julia> @btime test_kl(coxgroup(:F,4));  #julia 1.8
1.332 s (13934392 allocations: 2.27 GiB)
```

GAP3では、次の関数がW=F4の場合に11秒かかります。

```
test_kl:=function(W)local q,H,T,C;
  q:=X(Rationals);H:=Hecke(W,q^2,q);
  T:=Basis(H,"T");C:=Basis(H,"C'");
  List(Elements(W),e->T(C(e)));
end;
```

別のベンチマーク：

```benchmark
function test_kl2(W)
  el=elements(W)
  [KLPol(W,x,y) for x in el, y in el]
end

test_kl2 (generic function with 1 method)

julia>@btime test_kl2(coxgroup(:F,4)); # julia 1.9
4.307 s (42294917 allocations: 5.24 GiB)
```

GAP3では、次の関数がF4の場合に42秒かかります。

```
test_kl2:=function(W)local el;
  el:=Elements(W);
  List(el,x->List(el,y->KazhdanLusztigPolynomial(W,x,y)));
end;
```
