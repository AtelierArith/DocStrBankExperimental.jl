`UnipotentClasses(W[,p])`

`W` は Weyl 群の `FiniteCoxeterGroup` レコードまたは冪冪代数群 `𝐆` を記述する `rootdatum` である必要があります。この関数は、特性 `p` における `𝐆` の非可換類に関する情報を含むレコードを返します（省略された場合、`p` は `𝐆` にとって任意の良い特性であると仮定されます）。これには以下のフィールドが含まれます：

`group`: `W` へのポインタ

`p`: 非可換類が計算されたフィールドの特性。良い特性の場合は `0` です。

`orderclasses`: 非可換類に対して閉包関係によって誘導される部分順序の Hasse 図を記述するリスト。すなわち、`.orderclasses[i]` は $C̄ⱼ⊋ C̄ᵢ$ であり、かつ $C̄ⱼ⊋ C̄ₖ⊋ C̄ᵢ$ となるクラス $Cₖ$ が存在しない `j` のリストです。

`classes`: 各非可換類に関する情報を保持するレコードのリスト。これらのレコードの説明については [`UnipotentClass`](@ref) のヘルプを参照してください。

`springerseries`: 各々が `𝐆` の Springer 系列を記述するレコードのリスト。

個々の Springer 系列を記述するレコードには以下のフィールドがあります：

`levi`: Springer 系列が誘導される cuspidal local system `ι` が存在する Levi 部分群 `𝐋` に対応する反射のインデックス。

`relgroup`: 相対 Weyl 群 $N_𝐆(𝐋,ι)/𝐋$。最初の系列は `.levi=[]` かつ `.relgroup=W` の主系列です。

`locsys`: `nconjugacy_classes(.relgroup)` の長さを持つリストで、`i` 番目の位置に $N_𝐆(𝐋,ι)$ の `i` 番目のキャラクタに対応するローカルシステムを記述するペアが格納されています。ペアの最初の要素は関係する非可換類 `u` のインデックスであり、2 番目は `A(u)` の対応するキャラクタのインデックスです。

`Z`: Springer 系列に関連付けられた中心キャラクタで、中心の生成子に対するその値によって指定されます。

```julia-repl
julia> W=rootdatum(:sl,4)
sl₄

julia> uc=UnipotentClasses(W);

julia> uc.classes
5-element Vector{UnipotentClass}:
 UnipotentClass(1111)
 UnipotentClass(211)
 UnipotentClass(22)
 UnipotentClass(31)
 UnipotentClass(4)
```

非可換類の `show` 関数は `showtable` と `charnames` のすべてのオプションを受け入れます。オプション `mizuno` （または `shoji`）を指定すると、非可換類に対して Mizuno （または Shoji）によって与えられた名前が使用されます。さらに、相対 Weyl 群の各符号キャラクタでテンソル化された Springer 対応を提供するオプション `fourier` もあります。これは Fourier-Deligne 変換を介して得られる対応であり（ここでは `p` が非常に良いと仮定し、Lie 代数上に非退化の不変双線形形式が存在し、また非可換軌道を非可換類と同一視できるとします）。

以下は、Mizuno の記法を用いて `E₆` の非 cuspidal 部分の Springer 対応を表示する方法です。Weyl 群のキャラクタと Spaltenstein の `G₂` のキャラクタの記法を用いています（これは Spaltenstein の元の論文とデータを照合するのに便利です）：

```julia-rep1
julia> uc=UnipotentClasses(rootdatum(:E6sc));

julia> xdisplay(uc;cols=[5,6,7],spaltenstein=true,frame=true,mizuno=true,
      order=false)
┌──────┬─────────────────────────────────────────────────────┐
│u     │             E₆(Φ₁⁶) G₂(A₂×A₂Φ₁²)/ζ₃ G₂(A₂×A₂Φ₁²)/ζ₃²│
├──────┼─────────────────────────────────────────────────────┤
│E₆    │                1:1ₚ            ζ₃:1            ζ₃²:1│
│E₆(a₁)│                1:6ₚ           ζ₃:εₗ           ζ₃²:εₗ│
│D₅    │              Id:20ₚ                                 │
│A₅+A₁ │        -1:15ₚ 1:30ₚ           ζ₃:θ′           ζ₃²:θ′│
│A₅    │              1:15_q           ζ₃:θ″           ζ₃²:θ″│
│D₅(a₁)│              Id:64ₚ                                 │
│A₄+A₁ │              Id:60ₚ                                 │
│D₄    │              Id:24ₚ                                 │
│A₄    │              Id:81ₚ                                 │
│D₄(a₁)│111:20ₛ 3:80ₛ 21:90ₛ                                 │
│A₃+A₁ │              Id:60ₛ                                 │
│2A₂+A₁│               1:10ₛ          ζ₃:ε_c          ζ₃²:ε_c│
│A₃    │             Id:81ₚ′                                 │
│A₂+2A₁│             Id:60ₚ′                                 │
│2A₂   │              1:24ₚ′            ζ₃:ε            ζ₃²:ε│
│A₂+A₁ │             Id:64ₚ′                                 │
│A₂    │      11:15ₚ′ 2:30ₚ′                                 │
│3A₁   │            Id:15_q′                                 │
│2A₁   │             Id:20ₚ′                                 │
│A₁    │              Id:6ₚ′                                 │
│1     │              Id:1ₚ′                                 │
└──────┴─────────────────────────────────────────────────────┘
```
