```julia
SLVector(::NamedTuple)
SLVector(kwargs)
```

`SLArray`の標準コンストラクタ。

```julia
julia> SLVector(a = 1, b = 2, c = 3)
3-element SLArray{Tuple{3},1,(:a, :b, :c),Int64}:
 1
 2
 3
```

一部のアイテムを変更したコピーを構築することは、最初の引数がソースであり、追加のキーワード引数が変更を示すキーワードコンストラクタによってサポートされています。

```julia
julia> v1 = SLVector(a = 1.1, b = 2.2, c = 3.3);

julia> v2 = SLVector(v1; b = 20.20, c = 30.30)
3-element SLArray{Tuple{3},Float64,1,3,(:a, :b, :c)}:
  1.1
 20.2
 30.3
```

追加の例：

```julia
SLVector((a = 1, b = 2))
SLVector(a = 1, b = 2)
```
