`degrees(WF::Spets)`

`W` を反射コセト `WF` の群とし、`V` を `W` が反射群として作用する次元 `rank(W)` のベクトル空間とします。`f₁,…,fₙ` を `V` の対称代数 `SV` における `W` の基本不変量とし、これらは行列 `WF.F` の固有ベクトルとして選ぶことができます。対応する固有値は `V` 上で作用する `F` の *因子* と呼ばれ、コセトを特徴付けます –– それらは自明なコセトに対してのみ 1 に等しくなります。`WF` の *一般化次数* は、反射次数と対応する因子から形成されるペアです。

```julia-repl
julia> W=coxgroup(:E,6)
E₆

julia> WF=spets(W)
E₆

julia> phi=W(6,5,4,2,3,1,4,3,5,4,2,6,5,4,3,1);

julia> HF=subspets(WF,2:5,phi)
E₆₍₂₃₄₅₎=³D₄Φ₃

julia> diagram(HF)
ϕ acts as (1,2,4) on the component below
  O 2
  ￨
O—O—O D₄
1 3 4

julia> degrees(HF)
6-element Vector{Tuple{Int64, Cyc{Int64}}}:
 (1, ζ₃)
 (1, ζ₃²)
 (2, 1)
 (4, ζ₃)
 (6, 1)
 (4, ζ₃²)
```
