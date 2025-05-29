```
iA = IntegralArray([buffer,] A)
```

入力配列 `A` の積分配列を構築します。同じ形状のバッファが提供されている場合、これは非アロケーション版です。

積分配列は、各セルにその上と左にあるすべてのセルの合計を割り当てることによって計算されます。つまり、原点からピクセル位置までの長方形です。たとえば、1次元の場合、`iA[i] = sum(A[1:i])` となります。ベクトル `A` の原点が1の場合です。

```jldoctest; setup=:(using IntegralArrays)
julia> A = collect(reshape(1:25, 5, 5))
5×5 Matrix{Int64}:
 1   6  11  16  21
 2   7  12  17  22
 3   8  13  18  23
 4   9  14  19  24
 5  10  15  20  25

julia> iA = IntegralArray(A)
5×5 IntegralArray{Int64, 2, Matrix{Int64}}:
  1   7   18   34   55
  3  16   39   72  115
  6  27   63  114  180
 10  40   90  160  250
 15  55  120  210  325

julia> iA[3, 3] == sum(A[1:3, 1:3])
true

julia> iA[3..5, 3..5] == sum(A[3:5, 3:5])
true

julia> IntegralArray(A, A); # in-place modifying A itself

julia> A
5×5 Matrix{Int64}:
  1   7   18   34   55
  3  16   39   72  115
  6  27   63  114  180
 10  40   90  160  250
 15  55  120  210  325
```

閉区間 `a..b` は、異なるインデックスセマンティクスを持つ積分配列 `iX` をサポートするために使用されます。`iX[a:b]` は `iX` の部分配列を返し、`iX[a..b]` は元の配列 `X` の領域 `a:b` にわたる合計を計算します。`a ± σ`（`\pm<tab>` で入力可能）は、閉区間 `a-σ..a+σ` の便利なコンストラクタです。

画像から抽出されたすべてのブロックの合計/平均を計算する必要がある場合、積分配列を事前に構築することで、通常はより効率的な計算が提供されます。

```julia
using BenchmarkTools, IntegralArrays

# 簡略化された3x3平均フィルタ; デモ目的のみ
function mean_filter_naive!(out, X)
    Δ = CartesianIndex(1, 1)
    for i in CartesianIndex(2, 2):CartesianIndex(size(X).-1)
        block = @view X[i-Δ: i+Δ]
        out[i] = mean(block)
    end
    return out
end
function mean_filter_integral!(out, X)
    iX = IntegralArray(X)
    for i in CartesianIndex(2, 2):CartesianIndex(size(X).-1)
        x, y = i.I
        out[i] = iX[x±1, y±1]/9
    end
    return out
end

X = Float32.(rand(1:5, 64, 64));
m1 = copy(X);
m2 = copy(X);

@btime mean_filter_naive!($m1, $X); # 65.078 μs (0 allocations: 0 bytes)
@btime mean_filter_integral!($m2, $X); # 12.161 μs (4 allocations: 16.17 KiB)
m1 == m2 # true
```
