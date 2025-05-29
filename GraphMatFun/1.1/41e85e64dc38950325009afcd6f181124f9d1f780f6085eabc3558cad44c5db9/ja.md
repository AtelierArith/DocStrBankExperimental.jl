```
degopt=Degopt(x,y)
degopt=Degopt(HA,HB,y)
degopt=Degopt(graph)

struct Degopt{T}
    x::Vector{Tuple{Vector{T},Vector{T}}}
    y::Vector{T}
end
```

次数最適多項式を表すオブジェクトを作成します。すなわち、固定された乗算の数に対して次数を最大化する評価スキームにおける係数です。このオブジェクトは次の式の係数を表します。

```
A0=I
A1=A
A2=(x *A0+x *A1)(x *A0+x *A1)
A4=(x *A0+x *A1+x*A2)(x *A0+x *A1+x *A2)
A8=(x *A0+x *A1+x*A2)(x *A0+x *A1+x *A2)
 ..
```

および

```
Out=y*A0+y*A1+y*A4+y*A8+y*B4...
```

`x`の値は引数`x`に与えられ、これは各和の要素を含む`Vector{Tuple{Vector{T},Vector{T}}}`です。`y`ベクトルは出力を形成する要素を含みます。`HA`、`HB`、および`y`を使用したコンストラクタでは、`x`の要素が行列として保存されます。

[`graph_degopt`](@ref)によって生成されたグラフの係数は、`Degopt(graph)`を使用することで回復できます。
