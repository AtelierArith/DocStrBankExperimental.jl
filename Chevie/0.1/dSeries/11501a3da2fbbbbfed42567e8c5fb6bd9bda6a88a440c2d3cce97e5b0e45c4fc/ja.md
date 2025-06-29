`d`-ハリシュ＝チャンドラ系列は、有限還元群 $𝐆(𝔽_q)$ の非可換 `l`-ブロックを記述します（特に `l` があまり小さくない場合、つまり主に `𝐆` にとって悪くない素数の場合）。以下に述べる事実のいくつかはまだ部分的に予想の段階であり、何が確立され、何がまだ予想の段階であるかを正確に区別しようとはしません。

もし `(𝐋,λ)` が `d`-尖点対であれば、Lusztig によって誘導された $R_𝐋^𝐆(λ)$ の成分は `d`-ハリシュ＝チャンドラ系列と呼ばれ、$𝐆^F$ の `l`-ブロックの非可換部分を形成します。$𝐆^F$ の多様体 `𝐗` の `l`-進コホモロジーの $𝐆^F$-自己同型代数は、$W_𝐆(𝐋,λ):=N_𝐆(𝐋,λ)/𝐋$ のための `d`-サイクリックヘッケ代数 $H_𝐆(𝐋,λ)$ であると予想されています（いくつかのケースでは証明されています）。ここで `d`-サイクリックとは、$H_𝐆(𝐋,λ)$ のパラメータが `q` の単項式であり、$H_𝐆(𝐋,λ)$ が $q↦ζ_d$ のときの $W_𝐆(𝐋,λ)$ の代数に特化することを意味します。

したがって、Lusztig の誘導の分解は次の形になります：$R_𝐋^𝐆(λ)=∑_{ϕ∈Irr(W_𝐆(𝐋,λ))}(-1)^{nᵩ} ϕ(1)γᵩ$、ここで `γᵩ` は `ϕ` に付随する $𝐆^F$ の非可換キャラクタであり、`nᵩ` は `γᵩ` が現れる次数 $H^{nᵩ}_c(𝐗)$ です；さらに、任意の `ϕ` に対して $R_𝐋^𝐆(λ)(1)=  (-1)^{nᵩ} γᵩ(1)Sᵩ$ であり、ここで `Sᵩ` は `ϕ` に変形する $H_𝐆(𝐋,λ)$ のキャラクタのシュール要素です。関数 |Series| は `d`-ハリシュ＝チャンドラ系列を探索することを可能にします。

```julia-repl
julia> W=rootdatum("3D4")
³D₄

julia> l=cuspidal_data(W,3)
2-element Vector{@NamedTuple{levi::Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}, cuspidal::Int64, d::Root1}}:
 (levi = ³D₄, cuspidal = 8, d = ζ₃)
 (levi = ³D₄₍₎=Φ₃², cuspidal = 1, d = ζ₃)

julia> Series(W,l[2]...)
ζ₃-series R^³D₄_{³D₄₍₎=Φ₃²}(λ==Id)  H_G(L,λ)==hecke(G₄,Vector{Mvp{Cyc{Int64}, Int64}}[[ζ₃q², ζ₃, ζ₃q]])
┌─┬───────────────────────┐
│ │    γᵩ    φ  ε family #│
├─┼───────────────────────┤
│1│  φ₁‚₀ φ₁‚₀  1        1│
│2│  φ₁‚₆ φ₁‚₄  1        2│
│3│  φ₂‚₂ φ₁‚₈ -1        5│
│6│ φ″₁‚₃ φ₂‚₅  1        4│
│5│ φ′₁‚₃ φ₂‚₃ -1        3│
│7│  φ₂‚₁ φ₂‚₁ -1        5│
│4│³D₄[1] φ₃‚₂  1        5│
└─┴───────────────────────┘
```

上記では、$R_𝐓^𝐆(Id)$ に対応する 3-系列を探索しています。ここで `𝐆` はトライアリティ群で、`𝐓` はタイプ `(q²+q+1)²` のトーラスです。群 $W_𝐆(𝐓)$ は複素反射群 `G₄` です。表示は 'γᵩ' 列に $R_𝐓^𝐆(Id)$ の非可換キャラクタ成分の名前を示し、最初の列には非可換キャラクタのリストにおけるこれらのキャラクタの数を示しています。'φ' 列には非可換キャラクタ `γᵩ` に対応する $W_𝐆(𝐓)$ のキャラクタの名前が示され、'ε' 列には符号 $(-1)^{nᵩ}$ を示しています。最後の列には `γᵩ` がどの非可換キャラクタのファミリーに属するかを示しています。

`d`-ハリシュ＝チャンドラ系列の理論は、いくつかの公理を使用して特殊な複素反射群に一般化できます。以下に例を示します。

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> l=cuspidal_data(W,3)
5-element Vector{@NamedTuple{levi::Spets{PRSG{Cyc{Rational{Int64}}, Int16}}, cuspidal::Int64, d::Root1}}:
 (levi = G₄, cuspidal = 3, d = ζ₃)
 (levi = G₄, cuspidal = 6, d = ζ₃)
 (levi = G₄, cuspidal = 7, d = ζ₃)
 (levi = G₄, cuspidal = 10, d = ζ₃)
 (levi = G₄₍₎=Φ₁Φ′₃, cuspidal = 1, d = ζ₃)

julia> Series(W,l[5]...)
ζ₃-series R^G₄_{G₄₍₎=Φ₁Φ′₃}(λ==Id)  W_G(L,λ)==Z₆
┌─┬────────────────────────────────────┐
│ │   γᵩ φ(mod 3)  ε parameter family #│
├─┼────────────────────────────────────┤
│1│ φ₁‚₀        1  1      ζ₃q²        1│
│5│ φ₂‚₃       ζ₆  1      -ζ₃q        2│
│2│ φ₁‚₄       ζ₃ -1        ζ₃        4│
│8│ Z₃:2       -1 -1     -ζ₃²q        2│
│9│Z₃:11      ζ₃² -1       ζ₃²        4│
│4│ φ₂‚₅      ζ₆⁵ -1       -ζ₃        4│
└─┴────────────────────────────────────┘
```

上記では、タイプ `(q-1)(q-ζ₃)` のトーラスの自明なキャラクタに対応する `3`-系列を探索しています。循環群 $W_𝐆(𝐋,λ)$ に対して、パラメータは表に表示されます。これは $W_𝐆(𝐋,λ)$ のキャラクタに関連付けられています。最後に、'φ' 列に現れる '(mod 3)' という言及は、この場合、公理が非可換キャラクタ `γᵩ` とキャラクタ `ϕ`（およびパラメータ）との間の対応に曖昧さを残すことを意味します：対応は 3 による平行移動までしか知られていません（この場合、すべての `ϕ` を `-1` で乗算するのと同じです）。

最後に、反射群またはコセット `W` が整数上で定義されていない場合、重要なのはサイクリック多項式ではなく、`W` の定義体上のそれらの因子です。この場合、$ζ_d$ を表す整数 `d` を引数として与えるのではなく、単位根を指定する必要があります。たとえば、上記のケースでは次のように異なる答えが得られます。

```julia-repl
julia> cuspidal_data(W,E(3,2))
5-element Vector{@NamedTuple{levi::Spets{PRSG{Cyc{Rational{Int64}}, Int16}}, cuspidal::Int64, d::Root1}}:
 (levi = G₄, cuspidal = 2, d = ζ₃²)
 (levi = G₄, cuspidal = 5, d = ζ₃²)
 (levi = G₄, cuspidal = 7, d = ζ₃²)
 (levi = G₄, cuspidal = 10, d = ζ₃²)
 (levi = G₄₍₎=Φ₁Φ″₃, cuspidal = 1, d = ζ₃²)
```
