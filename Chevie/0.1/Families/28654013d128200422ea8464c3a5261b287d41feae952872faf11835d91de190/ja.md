非可逆文字のファミリー

`χ` が `Irr(W)` を走り、`ρ` が非可逆文字を走るときの行列 $⟨Rᵪ,ρ⟩_{𝐆 ^F}$ のブロックは *ルスティグファミリー* と呼ばれます。`𝐆` が分割され、`W` がコクセター群であるとき、これらは `Irr(W)` 側の両側カジダン-ルスティグセルに対応します。分割されたスぺツェスの場合、これはスぺツィアルヘッケ代数のルキエブロックに対応します。スカラー積の行列 $⟨Rᵪ,ρ⟩_{𝐆 ^F}$ は、$𝐆 ^F$ 上の *文字シーフの特性関数* である $A_{ρ'}$ を用いて、正方行列 $⟨A_{ρ'},ρ⟩_{𝐆 ^F}$ に拡張できます。この正方行列はファミリーの *フーリエ行列* と呼ばれます。

Chevie の 'UnipotentCharacters' レコードには、各ファミリーに関する情報を含むファミリーレコードのリストである '.families' フィールドがあります。以下はその例です。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> uc=UnipotentCharacters(W);

julia> uc.families
3-element Vector{Family}:
 Family(D(𝔖 ₃),[5, 6, 4, 3, 8, 7, 9, 10],ennola=-5)
 Family(C₁,[1])
 Family(C₁,[2])

julia> uc.families[1]
Family(D(𝔖 ₃),[5, 6, 4, 3, 8, 7, 9, 10],ennola=-5)
ドリンドフェルダブルの 𝔖 ₃, ルスティグのバージョン
┌────────┬────────────────────────────────────────────────────┐
│label   │eigen                                               │
├────────┼────────────────────────────────────────────────────┤
│(1,1)   │    1 1//6  1//2  1//3  1//3  1//6  1//2  1//3  1//3│
│(g₂,1)  │    1 1//2  1//2     .     . -1//2 -1//2     .     .│
│(g₃,1)  │    1 1//3     .  2//3 -1//3  1//3     . -1//3 -1//3│
│(1,ρ)   │    1 1//3     . -1//3  2//3  1//3     . -1//3 -1//3│
│(1,ε)   │    1 1//6 -1//2  1//3  1//3  1//6 -1//2  1//3  1//3│
│(g₂,ε)  │   -1 1//2 -1//2     .     . -1//2  1//2     .     .│
│(g₃,ζ₃) │   ζ₃ 1//3     . -1//3 -1//3  1//3     .  2//3 -1//3│
│(g₃,ζ₃²)│  ζ₃² 1//3     . -1//3 -1//3  1//3     . -1//3  2//3│
└────────┴────────────────────────────────────────────────────┘

julia> charnames(uc)[uc.families[1].charNumbers]
8-element Vector{String}:
 "phi2,1"
 "phi2,2"
 "phi1,3''"
 "phi1,3'"
 "G2[1]"
 "G2[-1]"
 "G2[E3]"
 "G2[E3^2]"
```

フーリエ行列は 'fourier(f)' によって得られます。フィールド 'f.charNumbers' にはファミリーに含まれる非可逆文字のインデックスが保持されています。これらの非可逆文字のフロベニウスの固有値のリストは 'Eigenvalues(f)' によって得られます。フーリエ行列と固有値ベクトルは *融合データ* の特性を満たします。フィールド 'f.charLabels' はファミリーを表示する際に 'labels' 列に表示されるものです。これはフーリエ行列の行に自然に付随するラベルを含んでいます。冗長群の場合、ファミリーは常に小さな有限群の "drinfeld_double" に付随し、'.charLabels' はこの構成から来ています。
