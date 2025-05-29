function GridInfo(N*real::NTuple{N, Int}, w::NTuple{N, Int}, periodicity::NTuple{N, Bool}, extra*pad::NTuple{N, Int}, L::NTuple{N, T}) where{N, T<:Union{Float32, Float64}}

```
この関数は、2つの可変配列を持つGridBoxオブジェクトを作成します。

N_real: 各方向の実グリッドポイントの数
w: ウィンドウ関数のカットオフのための各方向のグリッドポイントの数
periodicity: 各方向のグリッドが周期的かどうかを示す3つのブール値のタプル、パディングの有無を決定するため
extra_pad: パディングのための各方向の追加グリッドポイントの数
L: 各方向のボックスの長さ
h: 各方向のグリッド間隔、最初のポイントは[h/2, 3h/2, ..., L - h/2]にあります
N_image: 画像グリッドの各方向のグリッドポイントの数、tuple([2 * w[i] + 2 for i in 1:N]...) .+ N_realによって与えられます
N_pad: 各方向のパディングされたグリッドポイントの数、tuple([2 * pad[i] * (periodicity[i] == false) for i in 1:N]...) .+ N_image .+ N_realによって与えられます
```
