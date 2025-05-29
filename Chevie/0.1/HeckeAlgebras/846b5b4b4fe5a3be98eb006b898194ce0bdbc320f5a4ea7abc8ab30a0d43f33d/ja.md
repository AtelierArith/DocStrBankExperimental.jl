`HeckeCoset`は`Hϕ`であり、`H`はあるコクセター群`W`のイワホリ・ヘッケ代数で、あるスぺッツ`Wϕ`の自己同型`ϕ`が`ϕ(T_w)=T_{ϕ(w)}`によって作用します。ウェイル群の場合、これはある`F`-安定ボレル部分群から`𝐆 ^F`への自明な表現の誘導の可換代数に対するフロベニウス自己同型の作用に対応します。

```julia-repl
julia> WF=rootdatum(:u,3)
u₃

julia> HF=hecke(WF,Pol(:v)^2;rootpara=Pol())
hecke(u₃,v²,rootpara=v)

julia> CharTable(HF)
CharTable(hecke(u₃,v²,rootpara=v))
┌───┬──────────┐
│   │ 111 21  3│
├───┼──────────┤
│111│  -1  1 -1│
│21 │-2v³  .  v│
│3  │  v⁶  1 v²│
└───┴──────────┘
```

Xuhua HeとSian Nieの研究のおかげで、'class_polynomials'はこれらのコサインに対しても意味を持ちます。これはそのようなキャラクターテーブルを計算するために使用されます。
