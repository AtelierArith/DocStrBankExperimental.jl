```
StructArray(A; unwrap = T->false)
```

既存の多次元配列またはイテレータ `A` から `StructArray` を構築します。

`unwrap` キーワード引数は、要素型 `T` の配列を再帰的に `StructArray` に変換するかどうかを決定する関数です。

# 例

## 基本的な使い方

```julia-repl
julia> A = rand(ComplexF32, 2,2)
2×2 Array{Complex{Float32},2}:
 0.694399+0.94999im  0.422804+0.891131im
 0.101001+0.33644im  0.632468+0.811319im

julia> StructArray(A)
2×2 StructArray(::Array{Float32,2}, ::Array{Float32,2}) with eltype Complex{Float32}:
 0.694399+0.94999im  0.422804+0.891131im
 0.101001+0.33644im  0.632468+0.811319im
```

## イテレータから

```julia-repl
julia> StructArray((1, Complex(i, j)) for i = 1:3, j = 2:4)
3×3 StructArray(::Array{Int64,2}, ::Array{Complex{Int64},2}) with eltype Tuple{Int64,Complex{Int64}}:
 (1, 1+2im)  (1, 1+3im)  (1, 1+4im)
 (1, 2+2im)  (1, 2+3im)  (1, 2+4im)
 (1, 3+2im)  (1, 3+3im)  (1, 3+4im)
```

## 再帰的なアンラップ

```julia-repl
julia> StructArray((1, Complex(i, j)) for i = 1:3, j = 2:4; unwrap = T -> !(T<:Real))
3×3 StructArray(::Array{Int64,2}, StructArray(::Array{Int64,2}, ::Array{Int64,2})) with eltype Tuple{Int64,Complex{Int64}}:
 (1, 1+2im)  (1, 1+3im)  (1, 1+4im)
 (1, 2+2im)  (1, 2+3im)  (1, 2+4im)
 (1, 3+2im)  (1, 3+3im)  (1, 3+4im)
```
