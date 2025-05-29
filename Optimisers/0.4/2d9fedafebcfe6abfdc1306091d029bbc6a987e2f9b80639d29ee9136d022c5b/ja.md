```
trainables(x, path = false)
```

`x`のすべての学習可能なパラメータに対する反復可能なオブジェクトを返します。つまり、[`trainable`](@ref Optimisers.trainable)を通じて到達可能なすべての数値配列（[`isnumeric`](@ref Optimisers.isnumeric)を参照）です。

モデル内で複数回出現するパラメータ（結びついた重み）は、出力には一度だけ表示されます。

`path = false`の場合、出力は数値配列のリストです。

`path = true`の場合、出力は`(KeyPath, AbstractArray)`のペアのリストであり、[`KeyPath`](@ref)は元の構造内の配列へのパスを表す型です。

単一のフラットベクトルを返す類似の操作については、[`destructure`](@ref)も参照してください。

# 例

```jldoctest
julia> struct MyLayer
         w
         b
       end

julia> Functors.@functor MyLayer

julia> Optimisers.trainable(x::MyLayer) = (; w = x.w,) # この例ではwのみが学習可能です

julia> x = MyLayer([1.0,2.0,3.0], [4.0,5.0,6.0]);

julia> trainables(x)
1-element Vector{AbstractArray}:
 [1.0, 2.0, 3.0]

julia> x = MyLayer((a=[1.0,2.0], b=[3.0]), [4.0,5.0,6.0]);

julia> trainables(x) # ネストされたパラメータを収集します
2-element Vector{AbstractArray}:
 [1.0, 2.0]
 [3.0]
```

```jldoctest
julia> x = (a = [1.0,2.0], b = (Dict("c" => [3.0, 4.0], "d" => 5.0), [6.0,7.0]));

julia> for (kp, y) in trainables(x, path = true)
           println(kp, " => ", y)
       end
KeyPath(:a,) => [1.0, 2.0]
KeyPath(:b, 1, "c") => [3.0, 4.0]
KeyPath(:b, 2) => [6.0, 7.0]

julia> getkeypath(x, KeyPath(:b, 1, "c"))
2-element Vector{Float64}:
 3.0
 4.0
```
