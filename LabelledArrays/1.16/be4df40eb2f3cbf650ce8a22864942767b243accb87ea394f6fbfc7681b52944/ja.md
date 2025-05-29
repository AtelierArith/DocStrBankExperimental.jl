```julia
@LVector タイプ名
```

`@LVector` マクロは、eltype と未定義の値を持つ次元 1 の `LArray` を作成します。ベクトルの長さは、与えられた名前の数と等しくなります。

`LArray` と同様に、ユーザーはベクトルを初期化し、後でその値を設定することができます。

```julia
A = @LVector Float64 (:a, :b, :c, :d)
A .= rand(4)
```

ベクトルを初期化し、同時にその値を設定するには、代わりに [`@LArray`](@ref) を使用してください：

```julia
b = @LArray [1, 2, 3] (:a, :b, :c)
```
