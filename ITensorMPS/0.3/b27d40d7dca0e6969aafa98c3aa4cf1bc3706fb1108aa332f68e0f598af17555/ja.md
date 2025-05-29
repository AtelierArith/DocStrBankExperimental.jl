```
MPO(os::OpSum, sites::Vector{<:Index}; splitblocks=true, kwargs...)
MPO(eltype::Type{<:Number}, os::OpSum, sites::Vector{<:Index}; splitblocks=true, kwargs...)
```

OpSumオブジェクト`os`を、`sites`によって与えられたインデックスを持つMPOに変換します。結果として得られるMPOは、インデックス`sites[1], sites[1]', sites[2], sites[2]'`などを持ちます。この変換は、OpSum項を加算することによって得られるMPOを圧縮するアルゴリズムによって行われ、しばしば最小限のボンド次元を達成します。

出力MPOの希望する要素型を最初の引数として渡すことで、オプションで指定できます。

キーワード引数`splitblocks`は、結果として得られるMPOのスパース性を制御します。デフォルトの`splitblocks=true`では、MPOのリンクインデックスが次元1のブロックに分割され、MPOがよりスパースになる可能性があります。

`splitblocks=false`では、リンク次元のブロックが共通の量子数に従ってできるだけ詰め込まれ、大きなブロックが作成されます。ITensors 0.3.19以前では、これがデフォルトの出力でしたが、一般的に`splitblocks=true`で出力されたMPOは、DMRGのようなアルゴリズムでより良いパフォーマンスをもたらすことがわかっています。

# 例

```julia
os = OpSum()
os += "Sz",1,"Sz",2
os += "Sz",2,"Sz",3
os += "Sz",3,"Sz",4

sites = siteinds("S=1/2",4)
H = MPO(os,sites)
H = MPO(Float32,os,sites)
H = MPO(os,sites; splitblocks=false)
```
