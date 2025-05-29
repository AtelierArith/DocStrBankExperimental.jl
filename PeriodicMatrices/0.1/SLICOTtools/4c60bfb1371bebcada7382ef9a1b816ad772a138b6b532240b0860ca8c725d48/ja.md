```
mb03bd!(job::AbstractChar, defl::AbstractChar, compq::AbstractChar, qind::AbstractVector{Int64}, k::Integer, n::Integer, h::Integer, 
        ilo::Integer, ihi::Integer, s::AbstractVector{Int64}, a::Array{Float64, 3}, q::Array{Float64, 3}, alphar::AbstractVector{Float64}, 
        alphai::AbstractVector{Float64}, beta::AbstractVector{Float64}, scal::AbstractVector{Int64}, 
        liwork::Integer, ldwork::Integer) -> (info::Int64, iwarn::Int64)

mb03bd!(job::AbstractChar, defl::AbstractChar, compq::AbstractChar, qind::AbstractVector{Int64}, k::Integer, n::Integer, h::Integer, 
        ilo::Integer, ihi::Integer, s::AbstractVector{Int64}, a::Array{Float64, 3}, q::Array{Float64, 3}, alphar::AbstractVector{Float64}, 
        alphai::AbstractVector{Float64}, beta::AbstractVector{Float64}, scal::AbstractVector{Int64}, 
        iwork::AbstractVector{Int64}, dwork::AbstractVector{Float64}) -> (info::Int64, iwarn::Int64)
```

一般化された行列積の固有値を求めます

```
          s[1]           s[2]                 s[k]
  A[:,:,1]     * A[:,:,2]     * ... * A[:,:,k]
```

ここで `A[:,:,h]` は上ヘッセンベルグ行列であり、`A[:,:,i]`（`i <> h`）は上三角行列です。周期的QZ法の二重シフトバージョンを使用します。さらに、`A` は周期的シュール形式に還元される場合があります：`A[:,:,h]` は上準三角行列であり、他のすべての因子 `A[:,:,i]` は上三角行列です。オプションとして、`A[:,:,h]` の2-by-2対角ブロックに対応する2-by-2三角行列は、その積が2-by-2対角行列になるように還元されます。

`compq = 'U'` または `compq = 'I'` の場合、直交因子が計算され、配列 `Q` に格納されます。したがって、`s[i] = 1` のとき、

```
                T
    Q[:,:,i](in)   A[:,:,i](in)   Q[:,:,mod(i,k)+1](in)
                                                        T 
=   Q[:,:,i](out)  A[:,:,i](out)  Q[:,:,mod(i,k)+1](out),
```

`s[i] = -1` のとき、

```
                         T
    Q[:,:,mod(i,k)+1](in)   A[:,:,i](in)   Q[:,:,i](in)
                                                        T 
=   Q[:,:,mod(i,k)+1](out)  A[:,:,i](out)  Q[:,:,i](out).
```

直交因子の部分生成は、配列 `qind` を介して実現できます。

詳細については、`MB03BD` のSLICOTドキュメントを参照してください。
