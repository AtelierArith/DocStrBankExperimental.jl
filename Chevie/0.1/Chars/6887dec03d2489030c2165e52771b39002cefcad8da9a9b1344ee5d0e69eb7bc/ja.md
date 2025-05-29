`induction_table(u,g)`

は、部分群 `u` の不可約表現の分解を、群 `g` に誘導したものを記述するオブジェクトを返します。repl や IJulia または Pluto では、親群の表現に対応する行と、部分群の表現に対応する列を持つテーブルが表示されます。返されるオブジェクトには、誘導テーブルを含む `Matrix{Int}` 型のフィールド `scalar` があり、他のフィールドには `u` と `g` のキャラクターテーブルから取得したラベリング情報が含まれています。

```julia-rep1
julia> g=Group([Perm(1,2),Perm(2,3),Perm(3,4)])
Group([(1,2),(2,3),(3,4)])

julia> u=Group( [ Perm(1,2), Perm(3,4) ])
Group([(1,2),(3,4)])

julia> induction_table(u,g)  #     needs "using GAP"
Induction table from Group((1,2),(3,4)) to Group((1,2),(2,3),(3,4))
┌───┬───────────────┐
│   │X.1 X.2 X.3 X.4│
├───┼───────────────┤
│X.1│  .   1   .   .│
│X.2│  .   1   1   1│
│X.3│  1   1   .   .│
│X.4│  1   .   1   1│
│X.5│  1   .   .   .│
└───┴───────────────┘
```

```julia-repl
julia> g=coxgroup(:G,2)
G₂

julia> u=reflection_subgroup(g,[1,6])
G₂₍₁₅₎=A₂

julia> t=induction_table(u,g)
Induction table from G₂₍₁₅₎=A₂ to G₂
┌─────┬────────┐
│     │111 21 3│
├─────┼────────┤
│φ₁‚₀ │  .  . 1│
│φ₁‚₆ │  1  . .│
│φ′₁‚₃│  1  . .│
│φ″₁‚₃│  .  . 1│
│φ₂‚₁ │  .  1 .│
│φ₂‚₂ │  .  1 .│
└─────┴────────┘
```

`IO` 属性はテーブルフォーマットメソッドに伝達できます。

```julia-rep1
julia> xdisplay(t;rows=[5],cols=[3,2])
Induction table from G₂₍₁₅₎=A₂ to G₂
┌─────┬────┐
│     │3 21│
├─────┼────┤
│φ₂‚₁ │.  1│
└─────┴────┘
```

`xdisplay(t;TeX=true)` を使用して、TeX 形式の誘導テーブルを作成することも可能です。

`induction_table` は、スペッツ（反射コセット）にも対応しています。
