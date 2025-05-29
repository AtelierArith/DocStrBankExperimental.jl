```
拡散方程式(K[; C, sym])
拡散方程式{m}(K[; C, sym])
```

非線形拡散方程式。

# 引数

  * `K`: 拡散率関数（`C`が指定されていない場合）または導電率関数、未知数に基づいて定義されます。

# キーワード引数

  * `C=nothing`: 任意の容量関数、未知数に基づいて定義されます。
  * `sym=:u`: 出力において未知の関数を表すために使用される記号。

# 型パラメータ

  * `m=1`: 空間次元の数：

      * 非放射状の1次元拡散の場合は1（デフォルト）；
      * 極座標または円筒座標における放射状拡散の場合は2；
      * 球座標における放射状拡散の場合は3。

# 例

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> eq = Fronts.DiffusionEquation(D)
∂u/∂t = ∂(D(u)*∂u/∂r)/∂r

julia> eq = Fronts.DiffusionEquation{2}(D)
∂u/∂t = 1/r*∂(r*D(u)*∂u/∂r)/∂r

julia> eq = Fronts.DiffusionEquation{3}(D, sym=:c)
∂c/∂t = 1/r²*∂(r²*D(c)*∂c/∂r)/∂r
```
