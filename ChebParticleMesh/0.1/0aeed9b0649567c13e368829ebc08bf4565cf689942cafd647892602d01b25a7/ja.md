function ChebCoef(f::Function, h::T, w::Int, ν::Int) where{T<:Union{Float32, Float64}}

```
この関数は、関数 f のチェビシェフ近似のための ChebCoef オブジェクトを作成します。

f: 補間される関数
h: グリッド間隔
w: ウィンドウ関数のカットオフのためのグリッドポイントの数
ν: チェビシェフ点の数
```
