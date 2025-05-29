```
ITensor([ElT::Type, ]::AbstractArray, inds; tol=0.0, checkflux=true)
```

入力配列とQNインデックスのコレクションからブロックスパースITensorを作成します。ゼロは削除され、非ゼロブロックは配列のゼロ値から決定されます。

オプションで、要素が許容誤差以下の場合に削除されるように許容誤差を設定できます。

デフォルトでは、非ゼロブロックのフラックスが互いに一貫していることを確認します。このチェックを無効にするには、`checkflux=false`を設定します。

# 例

```julia
julia> i = Index([QN(0)=>1, QN(1)=>2], "i");

julia> A = [1e-9 0.0 0.0;
            0.0 2.0 3.0;
            0.0 1e-10 4.0];

julia> @show ITensor(A, i', dag(i); tol = 1e-8);
ITensor(A, i', dag(i); tol = 1.0e-8) = ITensor ord=2
Dim 1: (dim=3|id=468|"i")' <Out>
 1: QN(0) => 1
 2: QN(1) => 2
Dim 2: (dim=3|id=468|"i") <In>
 1: QN(0) => 1
 2: QN(1) => 2
NDTensors.BlockSparse{Float64,Array{Float64,1},2}
 3×3
Block: (2, 2)
 [2:3, 2:3]
 2.0  3.0
 0.0  4.0
```
