```
LinkType(from,to,dir=2)
```

ネットワーク内のリンクの種類の特性を説明するLinkType構造体を作成します。

LinkTypeは、特定の種類のリンクを説明する基準のセットと考えてください。最初の2つの引数は、リンクの開始点と終了点のノードの状態をそれぞれ指定します。3番目の引数は、LinkTypeが1または2のいずれかであるかを指定し、*dir=1*はリンクタイプが有向（単方向）として解釈されるべきことを示し、*dir=2*は無向（双方向）として解釈されるべきことを示します。

このタイプのリンクの開始点と終了点のノードの状態は、さまざまな方法で指定できます。*from*または*to*の値が0または*である場合、対応するノードは任意の状態にあることができます。ノードの状態に対応する整数値は、ノードが対応する状態にある必要があることを意味します。整数の配列またはタプルは、ノードがリストされた状態のいずれかにある必要があることを意味します。

# 例

```jldoctest
julia> using Fastnet

julia> LinkType(3,4)
Links of the form:  (3) --- (4)

julia> LinkType(3,4,1)
Links of the form:  (3) --> (4)

julia> LinkType(3,4,2)
Links of the form:  (3) --- (4)

julia> LinkType("*",4)
Links of the form:  (any) --- (4)

julia> LinkType(4,0)
Links of the form:  (4) --- (any)

julia> LinkType((1,2),3)
Links of the form:  (1/2) --- (3)

julia> LinkType(4,[1,2],1)
Links of the form:  (4) --> (1/2)
```
