```julia
@LArray Eltype Size Names
@LArray Values Names
```

`@LArray` マクロは、`Names` ベクターから決定された名前と `Values` ベクターから決定された値を持つ `LArray` を作成します。そうでなければ、eltype とサイズを使用して未定義の値を持つ `LArray` を作成します。

```julia
A = @LArray [1, 2, 3] (:a, :b, :c)
A.a == 1
```

ユーザーは、次に次元を指定することで未定義の値を持つラベル付き配列を生成することもできます。このアプローチは、ユーザーが後で入力するために配列を事前に割り当てることを意図している場合に便利です。

```julia
A = @LArray Float64 (2, 2) (:a, :b, :c, :d)
W = rand(2, 2)
A .= W
A.d == W[2, 2]
```

ユーザーは、Names と Values を同時に設定するための代替コンストラクタを使用することもできます。

```julia
julia> z = @LArray [1.0, 2.0, 3.0] (a = 1:2, b = 2:3);

julia> z.b
2-element view(::Array{Float64,1}, 2:3) with eltype Float64:
 2.0
 3.0

julia> z = @LArray [1 2; 3 4] (a = (2, :), b = 2:3);

julia> z.a
2-element view(::Array{Int64,2}, 2, :) with eltype Int64:
 3
 4
```

LArray と SLArray のラベルは、シンボルのタプルを返す関数 `symbols` を使用してアクセスできます。
