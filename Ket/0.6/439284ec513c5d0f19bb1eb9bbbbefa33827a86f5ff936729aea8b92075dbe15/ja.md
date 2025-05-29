```
applymap!(result::Matrix, K::Vector{<:AbstractMatrix}, M::AbstractMatrix, temp::Matrix)
```

クローズドプロセス（CP）マップを、クローズオペレーター `K` によって行列 `M` に適用します。`result` と `temp` はサイズ `dout × dout` と `dout × din` の行列でなければならず、ここで `dout, din == size(K[1])` です。
