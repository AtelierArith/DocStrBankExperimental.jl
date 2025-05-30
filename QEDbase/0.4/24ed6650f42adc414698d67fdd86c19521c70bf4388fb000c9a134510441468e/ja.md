```
AbstractCoordinateTransformation
```

四運動量に作用することを想定した座標変換の抽象基本型。`trafo::AbstractCoordinateTransformation`のすべてのサブタイプは、以下のインターフェース関数を実装する必要があります。

  * `QEDbase._transform(trafo,p)`: `p`を変換します
  * `Base.inv(trafo)`: 逆変換を返します

## 例

インターフェース関数を定義することでインターフェースを実装します：

```jldoctest trafo_interface
julia> using QEDbase

julia> struct TestTrafo{T} <: AbstractCoordinateTransformation
           a::T
       end

julia> QEDbase._transform(trafo::TestTrafo,p) = trafo.a*p

julia> Base.inv(trafo::TestTrafo) = TestTrafo(inv(trafo.a))

```

`TestTrafo`は四運動量を変換するために使用できます：

```julia
julia> trafo = TestTrafo(2.0)
TestTrafo{Float64}(2.0)

julia> p = SFourMomentum(4,3,2,1)
4-element SFourMomentum with indices SOneTo(4):
 4.0
 3.0
 2.0
 1.0

julia> trafo(p) # 各成分を2.0倍します
4-element SFourMomentum with indices SOneTo(4):
 8.0
 6.0
 4.0
 2.0

julia> inv(trafo)(p) # 各成分を2.0で割ります
4-element SFourMomentum with indices SOneTo(4):
 2.0
 1.5
 1.0
 0.5
```
