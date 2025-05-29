`Series(W, L, cuspidal, d)`

反射コセットまたは群 `W` が代数群 `𝐆` に対応し、`cuspidal` が `𝐋` の `d`-カスピダルユニポテントキャラクタ `λ` に対応する場合、$R_𝐋^𝐆(λ)$ に対応する `d`-系列を構築します。結果 `s` は以下のフィールドと関数を持つレコードです：

`s.spets`: 反射群またはコセット `W`。

`s.levi`: サブコセット `L`。

`s.cuspidal`: `UnipotentCharacters(L)` における `λ` のインデックス。

`s.d`: `d` の値（`Root1`）。

`relative_group(s)`: 群 $W_𝐆(𝐋,λ)$。

`dSeries.RLG(s)`: $R_𝐋^𝐆(λ)$ によって与えられる `UnipotentCharacter`。

`dSeries.eps(s)`: `relative_group(s)` の各キャラクタ `φ` に対して、対応する構成要素 `γᵩ` のコホモロジーにおける符号 $(-1)^{n_φ}$。

`degree(s)`: `RLG(s)` の一般的な次数、`CycPol` として。

`charnumbers(s)`: `RLG(s)` の構成要素の `UnipotentCharacters(W)` におけるインデックス。

`hecke(s)`: ヘッケ代数 $H_𝐆(𝐋,λ)$。

関数 `Series` には別の形式があります：

`Series(<W> [,<d> [,<ad>]];k...)`

ここで、引数とキーワードによって説明されるカスピダルデータに対応する `Series` のベクトルを返します（`cuspidal_data` のヘルプを参照してください）。

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> Series(W,3;proper=true)
1-element Vector{Series}:
 ζ₃-series R^G₄_{G₄₍₎=Φ₁Φ′₃}(λ==Id)  W_G(L,λ)==Z₆

julia> s=Series(W,3,1)[1]
ζ₃-series R^G₄_{G₄₍₎=Φ₁Φ′₃}(λ==Id)  W_G(L,λ)==Z₆
┌─┬────────────────────────────────────┐
│ │   γᵩ φ(mod 3)  ε パラメータファミリー #│
├─┼────────────────────────────────────┤
│1│ φ₁‚₀        1  1      ζ₃q²        1│
│5│ φ₂‚₃       ζ₆  1      -ζ₃q        2│
│2│ φ₁‚₄       ζ₃ -1        ζ₃        4│
│8│ Z₃:2       -1 -1     -ζ₃²q        2│
│9│Z₃:11      ζ₃² -1       ζ₃²        4│
│4│ φ₂‚₅      ζ₆⁵ -1       -ζ₃        4│
└─┴────────────────────────────────────┘

julia> s.spets
G₄

julia> s.levi
G₄₍₎=Φ₁Φ′₃

julia> s.cuspidal
1

julia> s.d
Root1: ζ₃

julia> hecke(s)
hecke(G₆‚₁‚₁,Vector{Mvp{Cyc{Int64}, Int64}}[[ζ₃q², -ζ₃q, ζ₃, -ζ₃²q, ζ₃², -ζ₃]])

julia> degree(s)
ζ₃Φ₁Φ₂²Φ″₃Φ₄Φ₆

julia> dSeries.RLG(s)
[G₄]:<φ₁‚₀>-<φ₁‚₄>-<φ₂‚₅>+<φ₂‚₃>-<Z₃:2>-<Z₃:11>

julia> charnumbers(s)
6-element Vector{Int64}:
 1
 5
 2
 8
 9
 4

julia> dSeries.eps(s)
6-element Vector{Int64}:
  1
  1
 -1
 -1
 -1
 -1

julia> relative_group(s)
G₆‚₁‚₁
```
