```
A = JopFft(T, n...[; dims=()])
```

ここで `A` はフーリエ変換であり、Aの定義域は (T,n) です。`dims` が設定されていない場合、`A` はN次元のフーリエ変換であり、ここで `N=ndims(dom)` です。そうでない場合、`A` は `dims` で指定された次元に対するフーリエ変換です。

複素数から複素数への変換の場合: `range(A)::JetSpace`。実数から複素数への変換の場合: `range(A)::JetSpaceSymmetric`。通常、JopFft は `range(A)` の構築を担当します。この空間を手動で構築する必要がある場合、便利なメソッドを提供します:

```
R = symspace(JopLn{JopFft_df!}, T, symdim, n...)
```

ここで `T` は精度（一般的に `Float32` または `Float64`）、`n...` は `A` の定義域の次元、`symdim` はフーリエ変換される最初の次元です。

# 例

## 1D, 実数から複素数

```julia
A = JopFft(Float64,128)
m = rand(domain(A))
d = A*m
```

## 1D, 複素数から複素数

```julia
A = JopFft(ComplexF64,128)
m = rand(domain(A))
d = A*m
```

## 2D, 実数から複素数

```julia
A = JopFft(Float64,128,256)
m = rand(domain(A))
d = A*m
```

## 3D, 実数から複素数、最初の次元のみを変換

```julia
A = JopFft(Float64,128,256; dims=(1,))
m = rand(domain(A))
d = A*m
```
