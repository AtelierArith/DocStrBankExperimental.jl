```julia
SLArray{::Tuple}(::NamedTuple)
SLArray{::Tuple}(kwargs)
```

これらは `SLArray` の標準コンストラクタです。一般的なN次元ラベル付き配列の場合、ユーザーは `SLArray` コンストラクタの型パラメータにサイズ（`Tuple{dim1,dim2,...}`）を指定する必要があります：

```julia
julia> SLArray{Tuple{2, 2}}((a = 1, b = 2, c = 3, d = 4))
2×2 SLArray{Tuple{2, 2}, Int64, 2, 4, (:a, :b, :c, :d)} with indices SOneTo(2)×SOneTo(2):
 :a => 1  :c => 3
 :b => 2  :d => 4

julia> SLArray{Tuple{2, 2}}(a = 1, b = 2, c = 3, d = 4)
 2×2 SLArray{Tuple{2,2},2,(:a, :b, :c, :d),Int64}:
 1  3
 2  4
```

変更された要素を持つコピーを構築することは、最初の引数がソースであり、追加のキーワード引数が変更を示すキーワードコンストラクタによってサポートされています。

```julia
julia> ABCD = @SLArray (2, 2) (:a, :b, :c, :d);

julia> B = ABCD(1, 2, 3, 4);

julia> B2 = SLArray(B; c = 30)
2×2 SLArray{Tuple{2,2},Int64,2,4,(:a, :b, :c, :d)}:
 1  30
 2   4
```

追加の例：

```julia
SLArray{Tuple{2, 2}}((a = 1, b = 2, c = 3, d = 4))
```
