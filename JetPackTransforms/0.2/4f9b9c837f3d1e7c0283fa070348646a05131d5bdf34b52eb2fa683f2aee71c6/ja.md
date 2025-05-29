```
A = JopDct(T, n...[;dims=()])
```

ここで `A` はタイプ II 離散コサイン変換 (DCT) であり、T は A のドメインとレンジの要素タイプ、n は A のサイズです。 `dims` が設定されていない場合、`A` は N 次元 DCT であり、ここで `N=length(n)` です。そうでない場合、`A` は `dims` で指定された次元に対する DCT です。

# 例

## 1D

```julia
A = JopDct(Float64, 128)
m = rand(domain(A))
d = A*m
```

## 2D

```julia
A = JopDct(Float64, 128, 64)
m = rand(domain(A))
d = A*m
```

## 3D 配列に対する 2D 変換

```julia
A = JopDct(Float64,128,64,32;dims=(1,2))
m = rand(domain(A))
d = A*m
```

# 注意

  * アジョイントペアは `sqrt(2/N)` と `sqrt(2)` の因子を適用することによって達成されます。参照してください：

      * https://en.wikipedia.org/wiki/Discrete*cosine*transform
      * http://www.fftw.org/fftw3*doc/1d-Real*002deven-DFTs-*0028DCTs*0029.html#g*t1d-Real*002deven-DFTs-*0028DCTs*0029

```
